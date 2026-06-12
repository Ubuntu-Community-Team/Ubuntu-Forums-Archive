---
title: "Major X Session Crash"
date: 2012-01-10
forum: General Help
---

### Post by castironpants on 2012-01-10
I keep logging in and start using my laptop (11.10) (using FGLRX, if that matters) and then the screen will flicker, the top menu bar will go to old Gnome icons and and grey background, the theme and mouse pointer will change. Then, often, the whole thing will just log out. I've taken a look at my system log and I think this might be the relevant thing:

```
Jan 10 16:18:40 acer gnome-session[23472]: Gdk-WARNING: The program 'gnome-session' received an X Window System error.#012This probably reflects a bug in the program.#012The error was 'XI_BadDevice (invalid Device parameter)'.#012  (Details: serial 206 error_code 151 request_code 147 minor_code 48)#012  (Note to programmers: normally, X errors are reported asynchronously;#012   that is, you will receive the error a while after causing it.#012   To debug your program, run it with the --sync command line#012   option to change this behavior. You can then get a meaningful#012   backtrace from your debugger if you break on the gdk_x_error() function.)#012
```

I'll also submit this to the bug tracker I guess?

---

