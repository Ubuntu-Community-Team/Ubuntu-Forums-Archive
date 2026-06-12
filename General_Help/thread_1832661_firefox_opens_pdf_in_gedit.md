---
title: "firefox opens pdf in gedit"
date: 2011-08-25
forum: General Help
---

### Post by ilantal on 2011-08-25
If I download a  pdf file using firefox and then double click on it, it will open using evince as expected.
If I want to open it (instead of save it), the default seems to be gedit, which is clearly not good.
Inside firefox I went to Edit-> Preferences-> Applications-> PDF document and chose Use Document Viewer (default). This should have set it to evince, but the default of gedit still comes up.
Inside of firefox I could choose "other" and then go to /usr/share/applications and choose evince.desktop. That didn't work and next time around it came back with gedit as the only real choice, with no memory of evince.

This should be straight forward, so what is the correct way to do it?
Thanks,
Ilan

---

### Post by fdrake on 2011-08-25
> **ilantal said:**
> If I download a  pdf file using firefox and then double click on it, it will open using evince as expected.
If I want to open it (instead of save it), the default seems to be gedit, which is clearly not good.
Inside firefox I went to Edit-> Preferences-> Applications-> PDF document and chose Use Document Viewer (default). This should have set it to evince, but the default of gedit still comes up.
Inside of firefox I could choose "other" and then go to /usr/share/applications and choose evince.desktop. That didn't work and next time around it came back with gedit as the only real choice, with no memory of evince.

This should be straight forward, so what is the correct way to do it?
Thanks,
Ilan

i am not sure what isn't that tab for the firefox application plug-ins only? i may  be wrong.
anyway the correct path is:  /usr/bin/evince

the one that you select is a app-luncher.

---

### Post by ilantal on 2011-08-25
Thanks for the reply. The path you suggest was the first one I tried, but there is no evince application, just a shared library. I tried it but had no luck. There must be a front end to the shared library, but I can't find it.

---

### Post by fdrake on 2011-08-25
> **ilantal said:**
> Thanks for the reply. The path you suggest was the first one I tried, but there is no evince application, just a shared library. I tried it but had no luck. There must be a front end to the shared library, but I can't find it.

can you post this command in the terminal?

```

whereis evince

```

maybe your path is different that's why firefox is nit working. 
when i run /usr/bin/evince i start the pdf reader!

---

### Post by ilantal on 2011-08-25
Sorry, I tried it again and I can choose the shared library and it even works. However since it isn't an application, I can't choose the checkbox to make this the application which will be used hereafter. To drill down each time is worthless. I might just as well Save it and double click on it.

---

### Post by ilantal on 2011-08-25
Thanks for the "whereis" trick. That will be useful in the future. I always did a search on the disk which takes forever.

In any case, it didn't find anything useful beyond the shared library. So the real problem remains that I can't make it the default and replace the gedit.

---

### Post by fdrake on 2011-08-25
> **ilantal said:**
> Sorry, I tried it again and I can choose the shared library and it even works. However since it isn't an application, I can't choose the checkbox to make this the application which will be used hereafter. To drill down each time is worthless. I might just as well Save it and double click on it.

that's weird.Maybe you don't have the right path. I tried it with firefox and i was able to check and select the file...

your path must differ or something....    what is your output for my previous command?


edit:
try to reinstall the program:
```

sudo apt-get purge evince
sudo apt-get install evince

```

---

### Post by ilantal on 2011-08-25
The output is
evince: /usr/bin/evince /usr/lib/evince /usr/share/evince /usr/share/man/man1/evince.1.gz

I tried it yet again, just in case I missed something. If I drill down to usr/bin I can choose evince, but "Do this automatically for files like this from now on" is grayed out. The command itself will work, but the drilling process is more work than just saving it.

On your system, in /usr/bin is evince a shared library?

Thanks for all your help,
Ilan

---

### Post by fdrake on 2011-08-25
> **ilantal said:**
> The output is
evince: /usr/bin/evince /usr/lib/evince /usr/share/evince /usr/share/man/man1/evince.1.gz

I tried it yet again, just in case I missed something. If I drill down to usr/bin I can choose evince, but "Do this automatically for files like this from now on" is grayed out. The command itself will work, but the drilling process is more work than just saving it.

On your system, in /usr/bin is evince a shared library?

Thanks for all your help,
Ilan

we have the same paths actually. i am using an older firefox not the latest one dough.  maybe that makes a difference.  does this happen only with envice? or also with the other prog? maybe you need a sudo priviledge to changed it in the new version? cannot say sorry...

---

### Post by ilantal on 2011-08-25
Wow, if you are in Los Angles, it is 2AM. Go get some sleep!

I tried it on my laptop as well and exactly the same thing happens.

I think it must be connected to the fact that evince is a shared library, not an "executable". Apparently firefox will use it, if you insist, but it won't allow you to use it hereafter.

All other, normal, programs are fine - just evince with its shared library is a problem. It sounds like a bug (or design "feature") in firefox.

Thanks again,
Ilan

---

### Post by mart1n on 2011-09-08
I have the same issue with Firefox/Natty/Gnome. I use Adobe PDF reader and the latest Firefox (6). In the Applications tab all PDF extensions refer to acroread, the correct path, and some PDFs/pdfs do open in reader. but on occasion only gedit is the default setting, and you need to enter the path to acroread manually, every time. FF somehow fails to recognize the .pdf extension and does not allow to enter new extensions (e.g. small caps pdf ).
Anybody a clue here? Seems a FF bug, but could also be Ubuntu Natty.

---

### Post by diversecg on 2011-11-16
I am experiencing this problem also, FF keeps trying to open with gedit, there is no other options.  I needed to set to use evince only.

Ubuntu 11.04 fully updated

---

### Post by ilantal on 2011-11-24
I found the answer to the gedit problem. Use Edit -> Preferences -> Applications. You'll find the content type PDF document and you can set it to whatever you want.

Ilan

---

### Post by jmciotat on 2012-03-02
Hi,

Same problem for me in Ubuntu 11.04 natty, firefox 10.0.2.

Last post suggesting to set Edit/Preferences/Applications does not work : it has been done for me (document PDF = Utiliser adobe reader 9 (par défaut))  and firefox keeps proposing only "gedit" (and only on some cases). It's really annoying.

---

### Post by bak&#305;r on 2012-03-15
Same problem. Gedit is somehow set as default program to open pdf files and cannot be changed. Any help will be appreciated.

---

### Post by MakisH on 2012-10-01
Same problem here, also with .rar files.
[This worked for me]("http://forums.opensuse.org/english/get-technical-help-here/applications/477775-firefox-opens-pdf-gedit.html"):
[QUOTE="Simeonof on forums.opensuse.org"]Go to ~/.local/share/applications/ folder and check its contents. If you  see the files mimeapps.list and defaults.list - delete them or move  them elsewhere. Restart firefox and voila. If you're curious - check the  contents of these files to try to find out what have put them there.[/QUOTE]

(but I don't really understand why :? )

---

### Post by Redoubts on 2012-10-10
> **MakisH said:**
> (but I don't really understand why :? )

A similar solution was [posted here]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/918019/comments/12"), providing a more complete explanation of what the change does. 

In short, you don't need to remove the whole [FONT="Courier New"]mimeapps.list[/FONT] file, just the line that says

[FONT="Courier New"]application/octet-stream=gedit.desktop;[/FONT]

---

### Post by gacb on 2012-12-21
It happens to me when opening a pdf from a Microsoft Help Attribution Definition File source. Opening others from the web isn't an issue.

---

