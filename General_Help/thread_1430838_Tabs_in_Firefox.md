---
title: "Tabs in Firefox"
date: 2010-03-15
forum: General Help
---

### Post by Skinny-Mini on 2010-03-15
I fixed a few problems after updating earlier but I now need help with the tabs in firefox. Sometimes, if I exit out of a tab in FF, the entire program shuts down. Why is that?

Running on Ubuntu 9.10.

---

### Post by n0dix on 2010-03-15
Run Firefox in safe mode from console: firefox --safe-mode.
Post the output of any error.
Which is the version of FF?

---

### Post by lovinglinux on 2010-03-15
Just type **about:config** in the address bar to get to the preferences, then search for **browser.tabs.closeWindowWithLastTab** and double-click it to set it as **false**. This should prevent it from closing when there is just only one tab open.

---

### Post by asmoore82 on 2010-03-15
> **Skinny-Mini said:**
> I fixed a few problems after updating earlier but I now need help with the tabs in firefox. Sometimes, if I exit out of a tab in FF, the entire program shuts down. Why is that?

Running on Ubuntu 9.10.

Sorry if this is dumb but I have to ask...
Is it the last open tab?

---

### Post by Skinny-Mini on 2010-03-15
@n0dix: I did that and it didn't exit out. Not sure which version I'm running.

@lovinglinux: Changed. Not sure if that's going to help, though.

@asmoore82: Yeah, usually.

---

### Post by soltanis on 2010-03-16
Skinny-Mini:

If you close the last open tab in Firefox, the default behavior is to exit the browser. If you want to change this, do what lovinglinux suggested.

If your browser suddenly closes when you are running Firefox and you close a tab that isn't the last tab, run firefox in a terminal, try to get it to crash, and show us the output.

You can find your firefox version with

```

firefox -v

```

In my case this outputs "Mozilla Firefox 3.5.8, Copyright (c) 1998 - 2010 mozilla.org"

---

### Post by Skinny-Mini on 2010-03-16
Version 3.5.7, apparently. 

And I'm running Firefox in the terminal and I currently can't get it to exit out again however the terminal keeps saying "(firefox:10710): Gdk-WARNING **: XID collision, trouble ahead"

---

### Post by soltanis on 2010-03-16
In my experience those GDK warnings are ignore-able.

Try upgrading to the latest Firefox version.

---

### Post by Skinny-Mini on 2010-03-16
I'll try to do that.

And it finally closed out again and I got the error. 

```
Gdk-ERROR **: The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 636496 error_code 158 request_code 148 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap (core dumped)
```

---

### Post by asmoore82 on 2010-03-16
> **Skinny-Mini said:**
> @asmoore82: Yeah, usually.

I believe it was in the jump from version 3 to 3.5 that this changed in Firefox:
Now the tab toolbar is always open and the last open tab can't be closed.

I understand why they did this: it would freak out "normal" people that the height
of the UI above web pages could change depending on the tab bar being open or not.
But I didn't like the change at first.
I don't really notice anymore, I have multiple tabs open 99% of the time anyway.

---

### Post by Skinny-Mini on 2010-03-16
So do I and I usually have to stay in fear of closing out of another tab.

---

### Post by heatblazer on 2010-03-18
That`s why I use Chrome.... :")

---

### Post by moneybox123 on 2010-03-18
I can not open new tab in Firefox:<

---

### Post by n0dix on 2010-03-18
> **moneybox123 said:**
> I can not open new tab in Firefox:<

This cannot look the same problem. Please, post a new thread.
Btw, are you get any error?

---

