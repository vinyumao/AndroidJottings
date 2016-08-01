1. 当给图片，布局设置背景图片时 如果imageview或layout的宽高为wrap_content时 图片和布局默认显示大小为背景图片大小，例子:一张.9图
大小超过了原本内容的大小 也就是布局里的内容大小没有.9图大小时 发现.9图显示过大 并没有根据内容来显示相应的大小 所以.9尺寸不应该过大
.9图的大小 要考虑内容在最少的时候的大小

2. 在fragment嵌套fragment时，获取子fragment时要用getChildFragmentManager; 另外在子fragment里findViewById时
不能用getActivity().findViewById(),应该用View.from(getActivity()).inflate()返回的view 去findviewbyid;如果不这样 在切换fargment时
用hide show 的方法 会出现显示错乱的问题；replace不会出现该问题

3. 布局文件根布局 宽高最好用match_parent,如 listview gridview 的item 布局 否则有可能出现显示不全的情况 例如listview 嵌套 gridView 虽然重写了gridview 但是 如果gridview的item根布局没有match_parent 会出现item显示不全的情况

4. onResume里获取不到 控件的坐标的，最好在onWindowFocusChanged方法里获取,如:
```
public void onWindowFocusChanged(boolean hasFocus) {
		super.onWindowFocusChanged(hasFocus);
		int [] location = new int[2];
		img.getLocationOnScreen(location);
		Log.i("onWindowFocusChanged", "img x:y " + location[0]+ ":" + location[1]);
	}```