---
title: "Need help running abgx360gui"
date: 2009-10-27
forum: General Help
---

### Post by GlitchCity on 2009-10-27
I downloaded a packaged version of abgx360gui here: [http://forums.xbox-scene.com/index.php?showtopic=681561](http://forums.xbox-scene.com/index.php?showtopic=681561)

This error came up when I ran it in the terminal: 

```
abgx360gui: error while loading shared libraries: **libwx_gtk2ud_richtext-2.8.so.0**: cannot open shared object file: No such file or directory
```Googled the above in bold and I couldn't find anything.

Any ideas what I can do?

---

### Post by GlitchCity on 2009-10-27
Bump.

---

### Post by alphaniner on 2009-10-27
My guess: you need one of the libwxgtk packages.  Do you have any such package installed?

Edit: Open Synaptic and type libwxgtk in the Quick Search box.  Another guess: if you need one of these packages it'll be libwxgtk2.8-0

---

### Post by GlitchCity on 2009-10-27
Thanks for your reply.  I do have libwxgtk2.8-0 installed, what is odd it contains libwx_**gtk2u**_richtext-2.8.so.0.5.0, but not libwx_**gtk2ud**_richtext-2.8.so which the app requires.

Have you come across this before?

---

### Post by alphaniner on 2009-10-27
I found an [old page]("http://sysinf0.klabs.be/usr/lib/libwx_gtk2ud_richtext-2.8.so.0?dist=;arch=") that suggested the file you need may be in the package libwxgtk2.8-dbg.


Unfortunately I don't know of any way to know what files are installed by a package without actually installing the package.

Another distro I used briefly allowed you to do this, it is a very handy function.

> Have you come across this before?

This is truly just educated guessing on my part. ;)

---

### Post by GlitchCity on 2009-10-27
You're a genius! :p  I came across that site when searching for that file, but somehow completely missed that package, now abgx360 gui works in Ubuntu!   Thank you for your help.

---

### Post by alphaniner on 2009-10-27
Happy to help.  Thank me by marking your thread Solved. :)

---

### Post by GlitchCity on 2009-10-27
You know what, I tried to do that before you even mentioned it, but I can't see it in advance edit.  How do you it?

---

### Post by Rasheeke on 2009-11-03
Hey, I'm also having troubles installing abgx360.  I got the wxWidgets version 2.9 and I get the following error when I run 'make' for abgx360

```

/usr/local/include/wx-2.9/wx/event.h: In member function ‘void PrettyButton::onMouseUp(wxMouseEvent&)’:
/usr/local/include/wx-2.9/wx/event.h:2872: error: ‘virtual bool wxEvtHandler::ProcessEvent(wxEvent&)’ is inaccessible
src/abgx360gui.cpp:175: error: within this context
src/abgx360gui.cpp: In member function ‘void abgx360gui::CreateGUIControls()’:
src/abgx360gui.cpp:684: error: ‘wxSAVE’ was not declared in this scope
src/abgx360gui.cpp:723: error: ‘wxOPEN’ was not declared in this scope
src/abgx360gui.cpp:723: error: ‘wxFILE_MUST_EXIST’ was not declared in this scope
src/abgx360gui.cpp:723: error: ‘wxMULTIPLE’ was not declared in this scope
src/abgx360gui.cpp:725: error: ‘wxOVERWRITE_PROMPT’ was not declared in this scope
src/abgx360gui.cpp: In member function ‘void abgx360gui::MnuDeleteSettingsClick(wxCommandEvent&)’:
src/abgx360gui.cpp:1047: warning: ‘size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)’ is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
src/abgx360gui.cpp: In member function ‘void abgx360gui::MyRegionButtonClick(wxCommandEvent&)’:
src/abgx360gui.cpp:2036: warning: ‘size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)’ is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
src/abgx360gui.cpp: In member function ‘void abgx360gui::MatchOnlyButtonClick(wxCommandEvent&)’:
src/abgx360gui.cpp:2083: warning: ‘size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)’ is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
make[1]: *** [abgx360gui-abgx360gui.o] Error 1

```

---

### Post by GlitchCity on 2009-11-04
Download the .deb version of abgx360gui by clicking the link at the very top of this thread.  Make sure you have all the packages installed first including the one in[COLOR=Black] Alphaniner's post.  That's what I ended up using and it works.[/COLOR]

---

### Post by wateenellende on 2012-02-02
> **alphaniner said:**
> 
Unfortunately I don't know of any way to know what files are installed by a package without actually installing the package.

Another distro I used briefly allowed you to do this, it is a very handy function.


Consult [http://packages.ubuntu.com](http://packages.ubuntu.com)
You can search packages and list their contents, or give a file name and search the contents of all packages to see which packages provide that file.

---

