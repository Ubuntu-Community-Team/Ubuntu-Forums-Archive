---
title: "Open Office Tanked"
date: 2010-06-29
forum: General Help
---

### Post by loaba on 2010-06-29
After spending the afternoon playing around with themes (thorough waste of time), it seems like I have somehow corrupted Open Office. Whenever I try to open any file type (word, excel, whatever), nothing happens. 

I've tried uninstalling/reinstalling via Synaptic, but that doesn't fix the problem.

As a Windows guy, at this point I'd probably just start over with a dirty install, does that apply to Linux as well? If I run the setup again, will I be able to save my files and such? Do I have any other options other than this?

---

### Post by TeoBigusGeekus on 2010-06-29
Open a terminal, start openoffice from there and post us any error messages.

---

### Post by loaba on 2010-06-29
[LIST]loaba@motherubuntu:~$ openoffice
openoffice: command not found
loaba@motherubuntu:~$ [/LIST]

---

### Post by SoFl W on 2010-06-29
So you know the commands to start open office from the command line are:

```

 soffice -writer
 soffice -calc
 soffice -impress

```

Edit:  (I see you just asked!)

---

### Post by sharath.puranik on 2010-06-29
Either the previous post or just type this in the terminal
```
ooffice
```

---

### Post by loaba on 2010-06-29
Okay, using those commands, the various apps opened. One time. I tried the commands again and I get nothing. Also, file icons still don't respond.

---

### Post by loaba on 2010-06-29
```
soffice -writer
soffice -calc
soffice -impress
ooffice
```

They all yield nada. I will try a reboot.


Edit: wait - apparently I left one of the windows open... via command line, I can launch Calc and open files from there. File icons are still no workie however.

---

### Post by sharath.puranik on 2010-06-29
> **loaba said:**
> Okay, using those commands, the various apps opened. One time. I tried the commands again and I get nothing. Also, file icons still don't respond.

When you tried it and it didn't open where there any error messages??

---

### Post by loaba on 2010-06-29
No, but I think that was because one of the application menu windows was left open. I closed it and was then able to launch via those command line entries.

---

### Post by loaba on 2010-06-29
Recap - due to user error, I thought the command line wasn't working. I was wrong, I can launch open office via command line.

What I can't do is launch via individual file icons.

---

### Post by prshah on 2010-06-29
> **loaba said:**
> What I can't do is launch via individual file icons.

Right click any one icon, choose Properties-> Open With-> and ensure that the correct application type is selected (ie, for xls/ods=>'OpenOffice.org SpreadSheet', doc/odt=>'OpenOffice.org Writer", etc); if it is not, select it (click the radio button next to it), and choose Close.

Double-clicking the icon now should launch the relevant application.

Repeat for other document types.

Please post back if you need more details.

---

### Post by loaba on 2010-06-29
prshah - Properties settings were correct. Still no go. I tried removing and resetting, still no go.

---

### Post by prshah on 2010-06-29
> **loaba said:**
> prshah - Properties settings were correct. Still no go

Right click the xls/doc file; what is the FIRST option in the context menu? (It should be Open With OpenOffice.org Spreadsheet / Writer).

If it is, see if choosing it works. If it opens correctly, subsequently all should open correctly by just double-clicking as usual.

If it doesn't open, choose the "Open With" option, select the relevant application from the list, and click OK. Subsequently it should open normally.

If none of these work, then please post back with details for further steps.

---

### Post by loaba on 2010-06-29
> **prshah said:**
> Right click the xls/doc file; what is the FIRST option in the context menu? (It should be Open With OpenOffice.org Spreadsheet / Writer).

This is correct.

> **prshah said:**
> If it is, see if choosing it works. If it opens correctly, subsequently all should open correctly by just double-clicking as usual.

No go
> **prshah said:**
> If it doesn't open, choose the "Open With" option, select the relevant application from the list, and click OK. Subsequently it should open normally.

No go



I just unistalled Open Office via Synaptic and now I'm downloading the OOo 3.2.1 ISO from Sun/Oracle. Maybe a clean install from a "factory" image will fix the problem.

---

### Post by loaba on 2010-06-29
Negative on the reload. At this point I suspect that when I was building various engines like Murine and whatnot, I must have screwed up some function of the desktop environment.

Bummer. I think I will have reinstall the OS. Or can I just reinstall gnome?

---

### Post by prshah on 2010-06-30
> **loaba said:**
> I think I will have reinstall

One last thing to try before you take the step of re-installation.

a) Can you open your document from the command line? use ```
/usr/bin/ooffice /home/user/your_document_here.doc
```

b) Right click any ooffice document (eg DOC, XLS, whatever) choose "Open With"->"Custom Command"-"/usr/bin/ooffice %s"-Open. If this works, repeat the steps, but this time also select the "Remember" option.

I don't think re-installing gnome will help in any way; I'm sure we can troubleshoot our way out of this with a little patience and a lot of time.

---

