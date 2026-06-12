---
title: "Windows like UAC"
date: 2009-09-14
forum: General Help
---

### Post by callistino on 2009-09-14
Hi, I am new to the Ubuntu OS and so far I am liking it. The only problem I am having is that every time I am browsing the filesystem and open a file to edit it doesn't let me do it. Instead I have to sudo gedit to it. It is ok if you are doing it ocassionally but if you are constantly having to navigate to the location through terminal then I do not see the pint on havin an application like Nautilus.

What I would like is a feature that would let me open the file, and in case I have to edit it, let me save it by asking for my root password. Something similar to what happens when you try to open the Synaptic Package Manager. Macs have this feature and they use Unix as a core.

Any help will be appreciated.
By the way, I am using Jaunty x64.

---

### Post by Marlonsm on 2009-09-14
It's a matter of security. Always you'll change important files (like configuration ones) you need to use the root account, and that's why you need to type the password.
If it wasn't like this everybody would have access to every file, making the system much less safe.

If you want to change many files, open the terminal and run:
```
gksu nautilus
```
_Be extremely careful_, running Nautilus as root is dangerous, as it can change just about anything in the computer.

There is also a package that allows you to access Nautilus as root by right-clicking it, but I forgot how it's called.

---

### Post by kogger on 2009-09-14
Ubuntu's admin privileges are far more potent than Windows. I don't like UAC in Windows because the OS doesn't let you make dangerous changes anyway, but Ubuntu's restrictions are necessary to make sure you don't destroy your computer.

---

### Post by P4man on 2009-09-14
if your new to the OS, you may feel a need (or actually have a need) to browse everywhere, either to learn/try or perhaps to get things working or set up. Once you actually start using the OS just as an OS, you will rarely need admin privileges.

Anyway, that said, if you want an easier way, install nautilus-gksu in synaptic. It will let you right click a folder or file in nautilus to open it as root.

---

### Post by callistino on 2009-09-14
I understand all the security issues involved and I don't like the Windows UAC myself. I was just referencing it as an example even though UAC refers to OS changes like program installation and what I want doesn't have anything to do with that. I know that I can start nautilus as a superuser but I believe that is even more security risky.

What about if you open a file for inspection and accidentally type something and pres ctrl+s? That file will be saved if nautilus was opened as root. I think is way more secure to ask for password that way if you accidentally save you will know it and hopefully cancel the saving.

Again Macs have this feature and is nto risky at all. It only helps the user. there is not point on having a UI if you cannot use it fully and have to rely on terminal for everything.

thaks for the fast response.

---

### Post by CatKiller on 2009-09-14
> **callistino said:**
>  What about if you open a file for inspection and accidentally type something and pres ctrl+s?

Why, if you'd opened up a file for inspection, would you "accidentally" save it? Personally, I prefer the discipline of using a text viewer for viewing and a text editor for editing. Not everyone agrees, obviously. And there's only so much hand-holding you can reasonably expect. It's not like you can't just view system files with your text editor as a normal user anyway.

Anyway, the functionality you're after already exists. It's called [PolicyKit]("http://en.wikipedia.org/wiki/PolicyKit"). Some applications use it already, as you've noticed, but not all of them do. More applications will use it over time.

The usual warnings apply; be careful what you do as root.

Another personal favourite; make the root file browser uncomfortable to use. That way you won't forget what you're doing, and you won't be tempted to use it when you shouldn't. Having the background salmon-pink is a reasonable visual clue.

---

### Post by callistino on 2009-09-14
> Why, if you'd opened up a file for inspection, would you "accidentally" save it?

The possibility exists and is why I don't like the idea of browsing in superuser mode.

Thanks for the response. Is good to know about PolicyKit. In the mean time I will implement the super cute backgroung of salmon-pink for my root editing.

---

### Post by CatKiller on 2009-09-14
> **callistino said:**
> The possibility exists and is why I don't like the idea of browsing in superuser mode.

It's good that you don't like it. Seriously. Since there are much worse things that you might do than deliberately saving a file that you (as far as you know) haven't edited at all.

For reference, Gedit automatically creates a backup file of the previous contents of a file when you save a new version, so undoing the mistake that has you concerned is simply a case of copying the backup file (which has the same name but ends in ~) over the now-broken one. Recursively changing the permissions on the filesystem (as at least one poster here has done) isn't quite so easy to reverse. Be careful what you do as root.

---

