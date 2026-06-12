---
title: "amule error since update"
date: 2006-04-23
forum: General Help
---

### Post by kingmonkey on 2006-04-23
Hello,

I installed amule 2.1.1 from a deb from the amule forums. Since the update last week (may or may not be related?) I get the following error when starting amule or amuled up. Can someone point me in the right direction please? Dont really fancy compiling my own atm.

Thanks in advance.

amule: Symbol `_ZTV11wxSpinEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxTextCtrlBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxDatagramSocket' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxSlider' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxSocketServer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxCommandEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericValidator' has different size in shared object, consider re-linking
amule: Symbol `_ZTV20wxNavigationKeyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxFocusEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTI7wxSizer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxImage' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxSocketEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTreeCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListItem' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxTimerEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxGauge' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxRadioBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxChoice' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxListEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxNotifyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV15wxNotebookEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV5wxPen' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxZipInputStream' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTextCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxCloseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxSplitterWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxBrush' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxMouseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericTreeCtrl' has different size in shared object, consider re-linking
Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 102,wx containers,compatible with 2.4),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

---

### Post by Kethinov on 2006-04-23
I can't help you with amule, but I might suggest instead you try out gtk-gnutella as an alternative.

---

### Post by kingmonkey on 2006-04-24
can you run gtk-gnutella as a demon?

---

### Post by ow50 on 2006-04-24
I can help with aMule, but I suggest against gtk-gnutella.

All the output refers to wx. Are you using Breezy with the default wx version of 2.6.1.1.1ubuntu2? Is the version you downloaded for Breezy and Breezy's wx? Give a link to the package. There's many Ubuntu packages at aMule forums, some may be for wx 2.6.3 and some may just be crap.

---

### Post by kingmonkey on 2006-04-25
Thanks for your help.

---

