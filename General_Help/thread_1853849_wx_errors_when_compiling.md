---
title: "wx errors when compiling"
date: 2011-10-03
forum: General Help
---

### Post by X_Splinter on 2011-10-03
Hey guys I could use some help

I am trying to compile abgx360gui, every goes find in ./configure but when I type make I got this errors about some "wx" stuff not being declared.

```
make  all-am
make[1]: Entering directory `/home/x_splinter/Área de Trabalho/abgx360gui-1.0.2'
g++ -DHAVE_CONFIG_H -I.  -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DwxUSE_GUI=0 -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DwxUSE_GUI=0 -g -O2  -g -O2  -MT abgx360gui-abgx360gui.o -MD -MP -MF .deps/abgx360gui-abgx360gui.Tpo -c -o abgx360gui-abgx360gui.o `test -f 'src/abgx360gui.cpp' || echo './'`src/abgx360gui.cpp
In file included from /usr/include/wx-2.8/wx/window.h:23:0,
                 from /usr/include/wx-2.8/wx/toplevel.h:21,
                 from /usr/include/wx-2.8/wx/frame.h:19,
                 from src/abgx360gui.h:19,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/cursor.h: In constructor ‘wxBusyCursorSuspender::wxBusyCursorSuspender()’:
/usr/include/wx-2.8/wx/cursor.h:65:22: error: ‘wxIsBusy’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h:67:26: error: ‘wxBusyCursor’ has not been declared
/usr/include/wx-2.8/wx/cursor.h:67:58: error: ‘wxSetCursor’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h: In destructor ‘wxBusyCursorSuspender::~wxBusyCursorSuspender()’:
/usr/include/wx-2.8/wx/cursor.h:72:22: error: ‘wxIsBusy’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h:74:26: error: ‘wxBusyCursor’ has not been declared
/usr/include/wx-2.8/wx/cursor.h:74:56: error: ‘wxSetCursor’ was not declared in this scope
In file included from /usr/include/wx-2.8/wx/window.h:26:0,
                 from /usr/include/wx-2.8/wx/toplevel.h:21,
                 from /usr/include/wx-2.8/wx/frame.h:19,
                 from src/abgx360gui.h:19,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/region.h: In member function ‘bool wxRegionBase::Intersect(const wxRect&)’:
/usr/include/wx-2.8/wx/region.h:251:37: error: invalid use of incomplete type ‘struct wxRegion’
/usr/include/wx-2.8/wx/gdicmn.h:38:28: error: forward declaration of ‘struct wxRegion’
/usr/include/wx-2.8/wx/region.h: In member function ‘bool wxRegionBase::Subtract(const wxRect&)’:
/usr/include/wx-2.8/wx/region.h:256:36: error: invalid use of incomplete type ‘struct wxRegion’
/usr/include/wx-2.8/wx/gdicmn.h:38:28: error: forward declaration of ‘struct wxRegion’
/usr/include/wx-2.8/wx/region.h: In member function ‘bool wxRegionBase::Xor(const wxRect&)’:
/usr/include/wx-2.8/wx/region.h:261:31: error: invalid use of incomplete type ‘struct wxRegion’
/usr/include/wx-2.8/wx/gdicmn.h:38:28: error: forward declaration of ‘struct wxRegion’
In file included from /usr/include/wx-2.8/wx/toplevel.h:21:0,
                 from /usr/include/wx-2.8/wx/frame.h:19,
                 from src/abgx360gui.h:19,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/window.h: At global scope:
/usr/include/wx-2.8/wx/window.h:82:12: error: field ‘font’ has incomplete type
/usr/include/wx-2.8/wx/window.h:85:14: error: field ‘colFg’ has incomplete type
/usr/include/wx-2.8/wx/window.h:89:14: error: field ‘colBg’ has incomplete type
/usr/include/wx-2.8/wx/window.h:920:35: error: ‘wxUpdateUIEvent’ has not been declared
/usr/include/wx-2.8/wx/window.h:1116:30: error: ‘wxSysColourChangedEvent’ has not been declared
/usr/include/wx-2.8/wx/window.h:1117:24: error: ‘wxInitDialogEvent’ has not been declared
/usr/include/wx-2.8/wx/window.h:1118:25: error: ‘wxMouseEvent’ has not been declared
/usr/include/wx-2.8/wx/window.h:1133:13: error: ‘WXWidget’ does not name a type
/usr/include/wx-2.8/wx/window.h:1135:34: error: ‘WXWidget’ has not been declared
/usr/include/wx-2.8/wx/window.h:1230:26: error: field ‘m_cursor’ has incomplete type
/usr/include/wx-2.8/wx/window.h:1231:26: error: field ‘m_font’ has incomplete type
/usr/include/wx-2.8/wx/window.h:1232:26: error: field ‘m_backgroundColour’ has incomplete type
/usr/include/wx-2.8/wx/window.h:1233:26: error: field ‘m_foregroundColour’ has incomplete type
/usr/include/wx-2.8/wx/window.h:1240:26: error: field ‘m_updateRegion’ has incomplete type
/usr/include/wx-2.8/wx/window.h:562:39: error: ‘wxNavigationKeyEvent’ has not been declared
/usr/include/wx-2.8/wx/window.h: In member function ‘const wxRegion& wxWindowBase::GetUpdateRegion() const’:
/usr/include/wx-2.8/wx/window.h:761:54: error: ‘m_updateRegion’ was not declared in this scope
/usr/include/wx-2.8/wx/window.h: In member function ‘wxRegion& wxWindowBase::GetUpdateRegion()’:
/usr/include/wx-2.8/wx/window.h:762:42: error: ‘m_updateRegion’ was not declared in this scope
/usr/include/wx-2.8/wx/window.h: In member function ‘const wxCursor& wxWindowBase::GetCursor() const’:
/usr/include/wx-2.8/wx/window.h:850:48: error: ‘m_cursor’ was not declared in this scope
/usr/include/wx-2.8/wx/window.h: In member function ‘wxWindow* wxWindowBase::GetGrandParent() const’:
/usr/include/wx-2.8/wx/window.h:1547:31: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
In file included from /usr/include/wx-2.8/wx/frame.h:19:0,
                 from src/abgx360gui.h:19,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/toplevel.h: At global scope:
/usr/include/wx-2.8/wx/toplevel.h:119:1: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/toplevel.h:238:24: error: ‘wxCloseEvent’ has not been declared
/usr/include/wx-2.8/wx/toplevel.h:239:17: error: ‘wxSizeEvent’ has not been declared
/usr/include/wx-2.8/wx/toplevel.h:246:21: error: ‘wxActivateEvent’ has not been declared
/usr/include/wx-2.8/wx/toplevel.h:249:35: error: ‘wxUpdateUIEvent’ has not been declared
/usr/include/wx-2.8/wx/toplevel.h: In member function ‘virtual bool wxTopLevelWindowBase::IsActive()’:
/usr/include/wx-2.8/wx/toplevel.h:183:68: error: ‘FindFocus’ was not declared in this scope
/usr/include/wx-2.8/wx/toplevel.h: In member function ‘virtual bool wxTopLevelWindowBase::IsVisible() const’:
/usr/include/wx-2.8/wx/toplevel.h:235:53: error: ‘IsShown’ was not declared in this scope
/usr/include/wx-2.8/wx/toplevel.h: In member function ‘virtual void wxTopLevelWindowBase::DoGetScreenPosition(int*, int*) const’:
/usr/include/wx-2.8/wx/toplevel.h:273:27: error: ‘DoGetPosition’ was not declared in this scope
In file included from src/abgx360gui.h:19:0,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/frame.h: At global scope:
/usr/include/wx-2.8/wx/frame.h:53:1: error: expected class-name before ‘{’ token
In file included from src/abgx360gui.h:44:0,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/sizer.h: In member function ‘void wxSizerItem::SetMinSize(const wxSize&)’:
/usr/include/wx-2.8/wx/sizer.h:292:21: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
In file included from /usr/include/wx-2.8/wx/panel.h:15:0,
                 from src/abgx360gui.h:45,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/generic/panelg.h: At global scope:
/usr/include/wx-2.8/wx/generic/panelg.h:31:1: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/generic/panelg.h:74:17: error: ‘wxSizeEvent’ has not been declared
/usr/include/wx-2.8/wx/generic/panelg.h:83:5: error: ‘wxChildFocusEvent’ has not been declared
In file included from /usr/include/wx-2.8/wx/dcbuffer.h:15:0,
                 from src/abgx360gui.h:57,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/dcmemory.h: In member function ‘void wxMemoryDCBase::SelectObject(wxBitmap&)’:
/usr/include/wx-2.8/wx/dcmemory.h:35:16: error: invalid use of incomplete type ‘struct wxBitmap’
/usr/include/wx-2.8/wx/gdicmn.h:30:28: error: forward declaration of ‘struct wxBitmap’
/usr/include/wx-2.8/wx/dcmemory.h:36:16: error: invalid use of incomplete type ‘struct wxBitmap’
/usr/include/wx-2.8/wx/gdicmn.h:30:28: error: forward declaration of ‘struct wxBitmap’
In file included from src/abgx360gui.h:57:0,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/dcbuffer.h: At global scope:
/usr/include/wx-2.8/wx/dcbuffer.h:41:1: error: expected class-name before ‘{’ token
/usr/include/wx-2.8/wx/dcbuffer.h: In member function ‘void wxBufferedDC::UnMask()’:
/usr/include/wx-2.8/wx/dcbuffer.h:110:35: error: ‘GetDeviceOrigin’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h:112:13: error: invalid use of incomplete type ‘struct wxDC’
/usr/include/wx-2.8/wx/window.h:59:28: error: forward declaration of ‘struct wxDC’
/usr/include/wx-2.8/wx/dcbuffer.h:112:34: error: invalid use of incomplete type ‘struct wxBitmap’
/usr/include/wx-2.8/wx/gdicmn.h:30:28: error: forward declaration of ‘struct wxBitmap’
/usr/include/wx-2.8/wx/dcbuffer.h:112:56: error: invalid use of incomplete type ‘struct wxBitmap’
/usr/include/wx-2.8/wx/gdicmn.h:30:28: error: forward declaration of ‘struct wxBitmap’
/usr/include/wx-2.8/wx/dcbuffer.h: In member function ‘void wxBufferedDC::InitCommon(wxDC*, int)’:
/usr/include/wx-2.8/wx/dcbuffer.h:131:21: error: invalid use of incomplete type ‘struct wxDC’
/usr/include/wx-2.8/wx/window.h:59:28: error: forward declaration of ‘struct wxDC’
/usr/include/wx-2.8/wx/dcbuffer.h:132:34: error: invalid use of incomplete type ‘struct wxDC’
/usr/include/wx-2.8/wx/window.h:59:28: error: forward declaration of ‘struct wxDC’
/usr/include/wx-2.8/wx/dcbuffer.h:132:56: error: ‘SetLayoutDirection’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h: At global scope:
/usr/include/wx-2.8/wx/dcbuffer.h:209:5: error: ‘wxPaintDC’ does not name a type
/usr/include/wx-2.8/wx/dcbuffer.h: In constructor ‘wxBufferedPaintDC::wxBufferedPaintDC(wxWindow*, wxBitmap&, int)’:
/usr/include/wx-2.8/wx/dcbuffer.h:167:11: error: class ‘wxBufferedPaintDC’ does not have any field named ‘m_paintdc’
/usr/include/wx-2.8/wx/dcbuffer.h:171:19: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/dcbuffer.h:171:32: error: ‘m_paintdc’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h:173:19: error: invalid use of incomplete type ‘struct wxBitmap’
/usr/include/wx-2.8/wx/gdicmn.h:30:28: error: forward declaration of ‘struct wxBitmap’
/usr/include/wx-2.8/wx/dcbuffer.h:174:19: error: ‘m_paintdc’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h:176:19: error: ‘m_paintdc’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h: In constructor ‘wxBufferedPaintDC::wxBufferedPaintDC(wxWindow*, int)’:
/usr/include/wx-2.8/wx/dcbuffer.h:181:11: error: class ‘wxBufferedPaintDC’ does not have any field named ‘m_paintdc’
/usr/include/wx-2.8/wx/dcbuffer.h:185:19: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/dcbuffer.h:185:32: error: ‘m_paintdc’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h:187:15: error: ‘m_paintdc’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h: In static member function ‘static wxSize wxBufferedPaintDC::GetBufferedSize(wxWindow*, int)’:
/usr/include/wx-2.8/wx/dcbuffer.h:204:54: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/dcbuffer.h:205:54: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/dcbuffer.h: In function ‘wxDC* wxAutoBufferedPaintDCFactory(wxWindow*)’:
/usr/include/wx-2.8/wx/dcbuffer.h:270:16: error: invalid use of incomplete type ‘struct wxWindow’
/usr/include/wx-2.8/wx/utils.h:51:28: error: forward declaration of ‘struct wxWindow’
/usr/include/wx-2.8/wx/dcbuffer.h:271:20: error: expected type-specifier before ‘wxPaintDC’
/usr/include/wx-2.8/wx/dcbuffer.h:271:20: error: cannot convert ‘int*’ to ‘wxDC*’ in return
/usr/include/wx-2.8/wx/dcbuffer.h:271:20: error: expected ‘;’ before ‘wxPaintDC’
/usr/include/wx-2.8/wx/dcbuffer.h:271:36: error: ‘wxPaintDC’ was not declared in this scope
/usr/include/wx-2.8/wx/dcbuffer.h:272:5: error: ‘else’ without a previous ‘if’
/usr/include/wx-2.8/wx/dcbuffer.h:273:44: error: cannot convert ‘wxBufferedPaintDC*’ to ‘wxDC*’ in return
In file included from src/abgx360gui.cpp:43:0:
src/abgx360gui.h: At global scope:
src/abgx360gui.h:98:26: error: ‘wxMouseEvent’ has not been declared
src/abgx360gui.h:99:22: error: ‘wxPaintEvent’ has not been declared
src/abgx360gui.h:100:9: error: ‘wxTipWindow’ does not name a type
src/abgx360gui.h:102:18: error: field ‘mLabel’ has incomplete type
In file included from src/abgx360gui.cpp:43:0:
src/abgx360gui.h:114:27: error: ‘wxMouseEvent’ has not been declared
src/abgx360gui.h:115:27: error: ‘wxMouseEvent’ has not been declared
src/abgx360gui.h:116:27: error: ‘wxMouseEvent’ has not been declared
src/abgx360gui.h:117:24: error: ‘wxMouseEvent’ has not been declared
src/abgx360gui.h:118:32: error: ‘wxEraseEvent’ has not been declared
src/abgx360gui.h:119:22: error: ‘wxPaintEvent’ has not been declared
src/abgx360gui.h:122:18: error: field ‘mNormalImage’ has incomplete type
src/abgx360gui.h:123:18: error: field ‘mOverImage’ has incomplete type
src/abgx360gui.h:124:18: error: field ‘mClickImage’ has incomplete type
src/abgx360gui.h:126:9: error: ‘wxCommandEvent’ does not name a type
src/abgx360gui.h:131:1: error: invalid use of incomplete type ‘struct wxFrame’
/usr/include/wx-2.8/wx/utils.h:50:28: error: forward declaration of ‘struct wxFrame’
src/abgx360gui.h:138:23: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:139:29: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:140:24: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:141:24: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:142:17: error: ‘wxUpdateUIEvent’ has not been declared
src/abgx360gui.h:143:30: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:144:34: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:145:32: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:146:32: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:147:31: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:148:36: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:149:34: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:150:34: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:151:33: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:152:28: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:153:35: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:154:24: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:155:32: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:156:35: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:157:34: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:158:37: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:160:28: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:161:29: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:162:28: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:163:33: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:164:40: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:165:38: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:166:30: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:167:33: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:168:26: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:169:31: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:170:37: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:171:31: error: ‘wxCommandEvent’ has not been declared
src/abgx360gui.h:178:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:179:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:180:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:181:3: error: ‘wxDirDialog’ does not name a type
src/abgx360gui.h:182:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:183:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:184:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:185:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:186:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:187:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:188:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:189:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:190:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:191:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:192:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:193:3: error: ‘wxFileDialog’ does not name a type
src/abgx360gui.h:195:3: error: ‘wxFileHistory’ does not name a type
src/abgx360gui.h:198:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:199:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:200:3: error: ‘wxStaticBitmap’ does not name a type
src/abgx360gui.h:202:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:203:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:204:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:205:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:206:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:207:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:209:3: error: ‘wxStaticBoxSizer’ does not name a type
src/abgx360gui.h:210:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:211:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:212:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:213:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:214:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:215:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:216:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:217:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:218:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:220:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:221:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:222:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:224:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:225:3: error: ‘wxRadioButton’ does not name a type
src/abgx360gui.h:226:3: error: ‘wxRadioButton’ does not name a type
src/abgx360gui.h:227:3: error: ‘wxRadioButton’ does not name a type
src/abgx360gui.h:228:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:230:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:231:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:232:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:233:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:234:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:235:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:236:3: error: ‘wxStaticBox’ does not name a type
src/abgx360gui.h:237:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:238:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:240:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:241:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:242:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:243:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:244:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:245:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:246:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:247:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:248:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:249:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:250:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:251:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:252:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:253:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:254:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:255:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:256:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:257:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:258:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:259:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:260:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:261:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:262:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:263:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:264:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:265:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:266:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:267:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:268:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:270:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:271:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:272:3: error: ‘wxStaticText’ does not name a type
src/abgx360gui.h:273:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:274:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:275:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:276:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:277:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:278:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:279:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:280:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:281:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:282:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:283:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:284:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:285:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:286:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:288:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:289:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:291:3: error: ‘wxNotebook’ does not name a type
src/abgx360gui.h:292:3: error: ‘wxBitmapButton’ does not name a type
src/abgx360gui.h:293:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:295:3: error: ‘wxTextCtrl’ does not name a type
src/abgx360gui.h:296:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:297:3: error: ‘wxCheckBox’ does not name a type
src/abgx360gui.h:298:3: error: ‘wxChoice’ does not name a type
src/abgx360gui.h:300:3: error: ‘wxStaticBoxSizer’ does not name a type
src/abgx360gui.h:304:3: error: ‘wxFileHistory’ does not name a type
src/abgx360gui.h:312:9: error: ‘wxStaticBitmap’ does not name a type
src/abgx360gui.h:466:16: error: ‘wxCloseEvent’ has not been declared
src/abgx360gui.cpp:80:5: error: invalid use of non-static member function ‘void InfoTip::onMouseOver(int&)’
src/abgx360gui.cpp:80:5: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:81:5: error: invalid use of non-static member function ‘void InfoTip::onPaint(int&)’
src/abgx360gui.cpp:81:5: error: ‘wxPaintEventHandler’ was not declared in this scope
src/abgx360gui.cpp: In constructor ‘InfoTip::InfoTip(wxWindow*, const wxBitmap&, const wxString&, const wxPoint&, const wxSize&)’:
src/abgx360gui.cpp:88:5: error: ‘mLabel’ was not declared in this scope
src/abgx360gui.cpp: At global scope:
src/abgx360gui.cpp:92:27: error: variable or field ‘onMouseOver’ declared void
src/abgx360gui.cpp:92:27: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:92:56: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:98:23: error: variable or field ‘onPaint’ declared void
src/abgx360gui.cpp:98:23: error: ‘wxPaintEvent’ was not declared in this scope
src/abgx360gui.cpp:98:37: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:111:5: error: invalid use of non-static member function ‘void PrettyButton::onEraseBackground(int&)’
src/abgx360gui.cpp:111:5: error: ‘wxEraseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:112:5: error: invalid use of non-static member function ‘void PrettyButton::onPaint(int&)’
src/abgx360gui.cpp:112:5: error: ‘wxPaintEventHandler’ was not declared in this scope
src/abgx360gui.cpp:113:5: error: invalid use of non-static member function ‘void PrettyButton::onMouseEnter(int&)’
src/abgx360gui.cpp:113:5: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:114:5: error: invalid use of non-static member function ‘void PrettyButton::onMouseLeave(int&)’
src/abgx360gui.cpp:114:5: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:115:5: error: invalid use of non-static member function ‘void PrettyButton::onMouseClick(int&)’
src/abgx360gui.cpp:115:5: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:116:5: error: invalid use of non-static member function ‘void PrettyButton::onMouseUp(int&)’
src/abgx360gui.cpp:116:5: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp: In constructor ‘PrettyButton::PrettyButton(wxWindow*, const wxBitmap&, const wxBitmap&, const wxBitmap&, const wxPoint&, const wxSize&, int)’:
src/abgx360gui.cpp:126:5: error: ‘mNormalImage’ was not declared in this scope
src/abgx360gui.cpp:127:5: error: ‘mOverImage’ was not declared in this scope
src/abgx360gui.cpp:128:5: error: ‘mClickImage’ was not declared in this scope
src/abgx360gui.cpp:130:5: error: ‘mEvent’ was not declared in this scope
src/abgx360gui.cpp:130:18: error: expected type-specifier before ‘wxCommandEvent’
src/abgx360gui.cpp:130:18: error: expected ‘;’ before ‘wxCommandEvent’
src/abgx360gui.cpp: At global scope:
src/abgx360gui.cpp:134:38: error: variable or field ‘onEraseBackground’ declared void
src/abgx360gui.cpp:134:38: error: ‘wxEraseEvent’ was not declared in this scope
src/abgx360gui.cpp:134:67: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:139:28: error: variable or field ‘onPaint’ declared void
src/abgx360gui.cpp:139:28: error: ‘wxPaintEvent’ was not declared in this scope
src/abgx360gui.cpp:139:42: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:149:33: error: variable or field ‘onMouseEnter’ declared void
src/abgx360gui.cpp:149:33: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:149:47: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:158:33: error: variable or field ‘onMouseLeave’ declared void
src/abgx360gui.cpp:158:33: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:158:62: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:166:33: error: variable or field ‘onMouseClick’ declared void
src/abgx360gui.cpp:166:33: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:166:62: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:173:30: error: variable or field ‘onMouseUp’ declared void
src/abgx360gui.cpp:173:30: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:173:59: error: expected primary-expression before ‘)’ token
make[1]: *** [abgx360gui-abgx360gui.o] Error 1
make[1]: Leaving directory `/home/x_splinter/Área de Trabalho/abgx360gui-1.0.2'
make: *** [all] Error 2

```

Thanks in advance for any info

---

### Post by X_Splinter on 2011-10-03
Please I really need help

---

### Post by X_Splinter on 2011-10-03
Solved :guitar:

---

### Post by ALiENr0x on 2011-11-05
> **X_Splinter said:**
> Solved :guitar:

i have the same problem, how had you solved?

---

### Post by X_Splinter on 2011-11-05
> **ALiENr0x said:**
> i have the same problem, how had you solved?

It's a problem with dependencies, I install it doing successfully after this
```
sudo apt-get install libcurl4-openssl-dev zlib1g-dev checkinstall
```

for the gui:

```
sudo apt-get install libwxgtk2.8-dev xterm
```

---

