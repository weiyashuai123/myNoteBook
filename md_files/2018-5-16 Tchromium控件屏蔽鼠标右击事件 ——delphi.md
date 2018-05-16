### Q：delphi cef3 的Tchromium控件屏蔽鼠标右击事件

* A：参考 [CEF3 怎样禁止右键菜单](http://www.cnblogs.com/micro-chen/p/5694978.html)</br>
解决：在Tchromium 的 BeforeContextMenu的事件处理中：
加入 model.clear;具体内容如下：</br>
```
procedure TMainForm.Chromium1BeforeContextMenu(Sender: TObject;
  const browser: ICefBrowser; const frame: ICefFrame;
  const params: ICefContextMenuParams; const model: ICefMenuModel);
begin
model.Clear;
end;
```
* 个人理解：</br>
delphi的 cef3 插件中Tchromium控件在右击时会弹出（pop）一个menu(popMenu) 此处在弹出右键菜单时通过model.Clear将该菜单清空，实现右击无效的效果，并不是最合适的解决方法，但是是最易理解与最快的。