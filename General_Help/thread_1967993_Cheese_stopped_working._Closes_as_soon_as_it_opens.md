---
title: "Cheese stopped working. Closes as soon as it opens"
date: 2012-04-28
forum: General Help
---

### Post by carys on 2012-04-28
[FONT=Arial Narrow]Cheese has always worked for me. About a week ago it started to close itself a second after[/FONT][FONT=Arial Narrow] it opens. 

[/FONT][FONT=monospace][FONT=Arial Narrow]This is what happens when I attempt to run it from the terminal..[/FONT]

carys@carys-RV410-RV510-S3510-E3510:~$ cheese

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:10581): Gdk-WARNING **: The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1092 error_code 9 request_code 137 minor_code 9)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)




[FONT=Arial Narrow]Anyone out there know how to solve this problem??[/FONT]
[/FONT]

---

### Post by josephmills on 2012-04-28
please open your terminal and enter in 
```
ubuntu-bug cheese 
```

that do you get back  After you are at launchpad ? 
here is a video on how to file a bug. take the steps then report back too us the bug thanks 
[http://www.youtube.com/watch?v=495V7FokwBU](http://www.youtube.com/watch?v=495V7FokwBU) 

thanks

---

