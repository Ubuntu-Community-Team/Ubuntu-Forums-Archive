---
title: "Make"
date: 2006-06-26
forum: General Help
---

### Post by souteneur3190 on 2006-06-26
```
/usr/include/kde/keditlistbox.h:60: warning: ‘class KEditListBox::CustomEditor’ has virtual functions but non-virtual destructor
kxmain.h:63: error: expected class-name before ‘{’ token
kxmain.h:63: warning: ‘class kxMain’ has virtual functions but non-virtual destructor
main.cpp: In function ‘int main(int, char**)’:
main.cpp:67: error: no matching function for call to ‘KApplication::setMainWidget(kxMain*&)’
/usr/share/qt3/include/qapplication.h:122: note: candidates are: virtual void QApplication::setMainWidget(QWidget*)
main.cpp:68: error: ‘class kxMain’ has no member named ‘show’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/malubankudi/Desktop/kxgenerator-0.2.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/malubankudi/Desktop/kxgenerator-0.2.3'
make: *** [all] Error 2
malubankudi@DellDesktop:~/Desktop/kxgenerator-0.2.3$

```

I get that error when trying to "make" the kde xorg editor.

---

### Post by mlind on 2006-06-27
looks like that build is broken or you're missing some dependency.

---

