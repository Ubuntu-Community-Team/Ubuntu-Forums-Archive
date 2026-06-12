---
title: "Extracting .rar packages?"
date: 2010-10-17
forum: General Help
---

### Post by fmuise on 2010-10-17
Is there a easy program that uses a GUI or am I going to need to do this from the terminal, either way I don't care I just need to be pointed in the right direction.

I installed the 7zip package and started using it in the terminal but I can't figure out how to insert a password into my command.

7z x <package> [LOCATION] ??

---

### Post by ron999 on 2010-10-17
Have you tried 'Right-click' then 'Extract here'?

---

### Post by 3rdalbum on 2010-10-17
1.7zip is not RAR. Install the 'unrar' package.

2. The regular archive manager in Ubuntu (file-roller) is a GUI for archive extraction. It uses the unrar package where available.

---

### Post by qamelian on 2010-10-17
If you've installed the full 7zip package, it should just work as a plugin to the default file-roller archive manager.

---

### Post by qamelian on 2010-10-17
> **3rdalbum said:**
> 1.7zip is not RAR. Install the 'unrar' package.

The 7zip-full package also includes the ability to work with RAR files. It's all I use.

---

### Post by fmuise on 2010-10-18
> **qamelian said:**
> The 7zip-full package also includes the ability to work with RAR files. It's all I use.

Yeah I was like wtf.


Umm okay, I have figured out the general use of unrar, but how would I tell it to sent it from say user\home\downloads to user\home\music??

---

### Post by sandyd on 2010-10-18
> **fmuise said:**
> Yeah I was like wtf.


Umm okay, I have figured out the general use of unrar, but how would I tell it to sent it from say user\home\downloads to user\home\music??
```

rar e /path/to/file /path/to/directory/you/want/to/extract/to

```

---

### Post by fmuise on 2010-10-18
> **sandyd said:**
> ```

rar e /path/to/file /path/to/directory/you/want/to/extract/to

```

and where would I enter the password switch because these archives have passwords.

---

### Post by qamelian on 2010-10-18
> **fmuise said:**
> and where would I enter the password switch because these archives have passwords.
Just double-click on the first RAR file in the series. The archive should open in file-roller. You can then either click on the extract button on the toolbar (which should bring up a file selector to allow you to navigate to your destination folder) or, if you already have the file manager open, drag the contents of the archive from the file-roller window to the destination folder in the file manager. File-roller should prompt you to provide the password before extraction begins.

---

### Post by ivanp on 2010-10-18
This could help
[http://www.pazmino.ec/quickfixes/unraring-files-on-linux.html](http://www.pazmino.ec/quickfixes/unraring-files-on-linux.html)

---

### Post by sandyd on 2010-10-18
> **fmuise said:**
> and where would I enter the password switch because these archives have passwords.
ill ask for the password

---

