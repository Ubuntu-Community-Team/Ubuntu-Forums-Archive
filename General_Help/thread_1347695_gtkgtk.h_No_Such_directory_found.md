---
title: "gtk/gtk.h No Such directory found"
date: 2009-12-06
forum: General Help
---

### Post by manishrana on 2009-12-06
I am using Ubuntu 9.10... I've some trouble withwindows programming..
I wrote a program in C..
Its just a simple program for creating a sample window.. program name is mywindow.c
But when i compiled it with :
gcc mywindow.c 'pkg-config --libs --cflags gtk+-2.0 '

or  by :

gcc mywindow.c 'pkg-config --libs --cflags gtk+-2.0' -o a.out


i got these :

gcc: pkg-config --libs --cflags gtk+-2.0: No such file or directory
mywindow.c:3:20: error: gtk/gtk.h: No such file or directory
mywindow.c: In function ‘main’:
mywindow.c:9: error: ‘GtkWidget’ undeclared (first use in this function)
mywindow.c:9: error: (Each undeclared identifier is reported only once
mywindow.c:9: error: for each function it appears in.)
mywindow.c:9: error: ‘p’ undeclared (first use in this function)
mywindow.c:11: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
mywindow.c:13: error: ‘gtk_main_quit’ undeclared (first use in this function)


my program is :
/*mywindow.c*/

#include<gtk/gtk.h>
#include<stdio.h>

int main(int argc,char *argv[])
{
 clrscr();
 GtkWidget *p;
 gtk_init(&argc,&argv);
 p = gtk_window_new(GTK_WINDOW_TOPLEVEL);
 gtk_window_set_title(p,"Sample Window");
 g_signal_connect(p,"destroy",gtk_main_quit,NULL);
 gtk_widget_set_size_request(p,300,300);
 gtk_window_show(p);
 gtk_main();
 return 0;
 getch();
} 

I've installed libgtk2.0-dev but still i doesnt work.. plz help..
A solution will be appreciated

---

### Post by pbrane on 2009-12-06
You need to back quote the pkg-config string like this:

```
`pkg-config --libs --cflags gtk+-2.0`
``` make sure you use the back quote character. that will cause the string to be executed. right now gcc thinks is is a file name. 

```
 gcc -o mywindow `pkg-config --libs --cflags gtk+-2.0` mywindow.c
```

should work.

Not sure why you have calls to clrscr() and getch() in main though. the program will return before the getch() function is called and clrscr() is not necessary. Also gtk_window_show() should be gtk_widget_show()

Try this code:

```

 1 #include<gtk/gtk.h>
 2 #include<stdio.h>
 3
 4 int main(int argc,char *argv[])
 5 {
 6   GtkWidget *p;
 7   gtk_init(&argc,&argv);
 8   p = gtk_window_new(GTK_WINDOW_TOPLEVEL);
 9   gtk_window_set_title(GTK_WINDOW(p),"Sample Window");
10   g_signal_connect(p,"destroy",gtk_main_quit,NULL);
11   gtk_widget_set_size_request(p,300,300);
12   gtk_widget_show(p);
13   gtk_main();
14   return 0;
15 }

```

---

