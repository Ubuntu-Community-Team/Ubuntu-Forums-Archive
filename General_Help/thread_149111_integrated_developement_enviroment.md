---
title: "integrated developement enviroment"
date: 2006-03-23
forum: General Help
---

### Post by gos1 on 2006-03-23
hi ; 
 which is the best editor for c++ at gnome does anyone know  ? 
and I have a problem compiling my c++ codes 
```

#include <iostream>
using namespace std;

main()
{
int x  ;
x = 4 ;
if (x < 3){
  cout << "Hello, world!" << endl;
}
else {
 cout << "did not work" << endl;
}
 
}

```
and get this after compiling
--------------------------
cd '/home/cem/deneme/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
make all-recursive
Making all in src
compiling deneme.cpp (g++)
linking deneme (libtool)
linking deneme (g++)
*** Success ***
--------------------------
but cannot execute it. 
does anyone know what the problem is ?

---

### Post by Casey on 2006-03-23
It depends what you want and how much work you want to put into customizing it.

Eclipse ([http://www.eclipse.org/]("http://www.eclipse.org/")) with the CDT plugin ([http://wiki.eclipse.org/index.php/CDT]("http://wiki.eclipse.org/index.php/CDT")) works quite well under gnome.

There's also Anjuta ([http://anjuta.sourceforge.net/]("http://anjuta.sourceforge.net/")) which was written for gnome.

Another option is KDevelop but since you specifically mentioned gnome I assume that won't be what you'd like.  Finally there's always vi/emacs/any text editor of choice, but I assume that's what you're using now.

---

### Post by ZylGadis on 2006-03-23
I recently stumbled across Code::Blocks, but I haven't had the time to try it. It looks like a good cpp IDE, maybe even on par with NetBeans for java. I'd love someone to give an opinion on it.

---

### Post by gos1 on 2006-03-24
I would like to have a graphical ide because want to design some little games for linux. I mean something like microsoft visual studio. do you know something similar to it.  well Kdevelop is but I cannot run my codes on that. I dont know what the problem is but guessing that it needs some libs coming with KDE

---

