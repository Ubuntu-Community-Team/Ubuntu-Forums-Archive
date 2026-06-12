---
title: "Compile errors while doing make"
date: 2009-08-14
forum: General Help
---

### Post by serpantman on 2009-08-14
Trying to install abgx360.

Had to install wx-widgets.

Now configure runs fine, but when i run make it gives me compile errors about things not being declared etc... Here is a small sample of the errors.

```

src/abgx360gui.h:247: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:248: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:248: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:249: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:249: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:250: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:250: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:251: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:251: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:252: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:252: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:253: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:253: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:254: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:254: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:256: error: ISO C++ forbids declaration of ‘wxChoice’ with no type
src/abgx360gui.h:256: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:257: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
src/abgx360gui.h:257: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:259: error: ISO C++ forbids declaration of ‘wxNotebook’ with no type
src/abgx360gui.h:259: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:260: error: ISO C++ forbids declaration of ‘wxBitmapButton’ with no type
src/abgx360gui.h:260: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:261: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
src/abgx360gui.h:261: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:263: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
src/abgx360gui.h:263: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:264: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:264: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:265: error: ISO C++ forbids declaration of ‘wxCheckBox’ with no type
src/abgx360gui.h:265: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:266: error: ISO C++ forbids declaration of ‘wxChoice’ with no type
src/abgx360gui.h:266: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:268: error: ISO C++ forbids declaration of ‘wxStaticBoxSizer’ with no type
src/abgx360gui.h:268: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:272: error: ISO C++ forbids declaration of ‘wxFileHistory’ with no type
src/abgx360gui.h:272: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:279: error: ISO C++ forbids declaration of ‘wxStaticBitmap’ with no type
src/abgx360gui.h:279: error: expected ‘;’ before ‘*’ token
src/abgx360gui.h:422: error: ‘wxCloseEvent’ has not been declared
src/abgx360gui.cpp:77: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:78: error: ‘wxPaintEventHandler’ was not declared in this scope
src/abgx360gui.cpp: In constructor ‘InfoTip::InfoTip(wxWindow*, const wxBitmap&, const wxString&, const wxPoint&, const wxSize&)’:
src/abgx360gui.cpp:85: error: ‘mLabel’ was not declared in this scope
src/abgx360gui.cpp: At global scope:
src/abgx360gui.cpp:89: error: variable or field ‘onMouseOver’ declared void
src/abgx360gui.cpp:89: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:89: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:95: error: variable or field ‘onPaint’ declared void
src/abgx360gui.cpp:95: error: ‘wxPaintEvent’ was not declared in this scope
src/abgx360gui.cpp:95: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:108: error: ‘wxEraseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:109: error: ‘wxPaintEventHandler’ was not declared in this scope
src/abgx360gui.cpp:110: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:111: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:112: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp:113: error: ‘wxMouseEventHandler’ was not declared in this scope
src/abgx360gui.cpp: In constructor ‘PrettyButton::PrettyButton(wxWindow*, const wxBitmap&, const wxBitmap&, const wxBitmap&, const wxPoint&, const wxSize&, int)’:
src/abgx360gui.cpp:123: error: ‘mNormalImage’ was not declared in this scope
src/abgx360gui.cpp:124: error: ‘mOverImage’ was not declared in this scope
src/abgx360gui.cpp:125: error: ‘mClickImage’ was not declared in this scope
src/abgx360gui.cpp:127: error: ‘mEvent’ was not declared in this scope
src/abgx360gui.cpp:127: error: expected type-specifier before ‘wxCommandEvent’
src/abgx360gui.cpp:127: error: expected `;' before ‘wxCommandEvent’
src/abgx360gui.cpp: At global scope:
src/abgx360gui.cpp:131: error: variable or field ‘onEraseBackground’ declared void
src/abgx360gui.cpp:131: error: ‘wxEraseEvent’ was not declared in this scope
src/abgx360gui.cpp:131: error: expected primary-expression before ‘)’ token
src/abgx360gui.cpp:136: error: variable or field ‘onPaint’ declared void
src/abgx360gui.cpp:136: error: ‘wxPaintEvent’ was not declared in this scope
src/abgx360gui.cpp:136: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:146: error: variable or field ‘onMouseEnter’ declared void
src/abgx360gui.cpp:146: error: ‘wxMouseEvent’ was not declared in this scope
src/abgx360gui.cpp:146: error: ‘event’ was not declared in this scope
src/abgx360gui.cpp:155: error: variable or field ‘onMouseLeave’ declared void
src/abgx360gui.cpp:155: error: ‘wxMouseEvent’ was not declared in this scope

```

What's wrong?

---

### Post by michy99 on 2009-08-14
When you get a long list of errors, look at the first one. The others usually follow from that one.

---

### Post by serpantman on 2009-08-14
```

make  all-am
make[1]: Entering directory `/home/axle/Desktop/abgx360gui-1.0.1'
g++ -DHAVE_CONFIG_H -I.  -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 
-D_LARGE_FILES -DwxUSE_GUI=0 -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS
=64 -D_LARGE_FILES -DwxUSE_GUI=0 -g -O2  -g -O2  -MT abgx360gui-abgx360gui.o -MD -MP -MF .deps/abgx360gui-abgx360gui.
Tpo -c -o abgx360gui-abgx360gui.o `test -f 'src/abgx360gui.cpp' || echo './'`src/abgx360gui.cpp
In file included from /usr/include/wx-2.8/wx/window.h:23,
                 from /usr/include/wx-2.8/wx/toplevel.h:21,
                 from /usr/include/wx-2.8/wx/frame.h:19,
                 from src/abgx360gui.h:19,
                 from src/abgx360gui.cpp:43:
/usr/include/wx-2.8/wx/cursor.h: In constructor ‘wxBusyCursorSuspender::wxBusyCursorSuspender()’:
/usr/include/wx-2.8/wx/cursor.h:65: error: ‘wxIsBusy’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h:67: error: ‘wxBusyCursor’ has not been declared
/usr/include/wx-2.8/wx/cursor.h:67: error: ‘wxSetCursor’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h: In destructor ‘wxBusyCursorSuspender::~wxBusyCursorSuspender()’:
/usr/include/wx-2.8/wx/cursor.h:72: error: ‘wxIsBusy’ was not declared in this scope
/usr/include/wx-2.8/wx/cursor.h:74: error: ‘wxBusyCursor’ has not been declared

```

That's the first part. I can't make out what wrong from that though :(.

---

### Post by serpantman on 2009-08-14
Anyone have an idea even? If i dont get this running i'll have to run the windows version in virtual box or with wine :(. That makes me a sad panda.

---

### Post by serpantman on 2009-08-14
Could i perhaps be missing a library file or something? Should i edit the source lol..... Do you guys need more info or maybe i should be posting in the suse forums :o

---

### Post by GlitchCity on 2009-10-27
That's exactly the error I'm getting when making.

Does anyone have a solution?

---

### Post by GlitchCity on 2009-10-28
Problem solved:

[http://ubuntuforums.org/showthread.php?t=1303098](http://ubuntuforums.org/showthread.php?t=1303098)

---

