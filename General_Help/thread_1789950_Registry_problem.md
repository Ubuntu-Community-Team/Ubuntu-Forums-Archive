---
title: "Registry problem"
date: 2011-06-24
forum: General Help
---

### Post by Weatherlawyer on 2011-06-24
I have a problem with opening folders in Ubuntu 10.10

The Home folder opens from "Places" with Image Viewer. The problem extends to other folders such as my USB drive, too.

I have just tried to open a text file from the search programme and it showed up as a Mailbox file. I have to open documents with a defined programme as in "Open With..."

I believe I can store files and folders in the Home folder. Though can't be sure they are being set up correctly there.

In the same menu trying to open "Desktop" gets me a can't open eye of Gnome dialogue:
Eye of Gnome Image Viewer      No images found in the 'file///home/myname/desktop'. 

Where can I get a utilities disc for Linux or preferably for Ubuntu 10.10?

MTIA.

Mike.

---

### Post by haqking on 2011-06-24
> **Weatherlawyer said:**
> [SIZE=2][FONT=Courier New]I have a problem with opening folders in Ubuntu 10.10

The Home folder opens from "Places" with Image Viewer. The problem extends to other folders such as my USB drive, too.

I have just tried to open a text file from the search programme and it showed up as a Mailbox file. I have to open documents with a defined programme as in "Open With..."

I believe I can store files and folders in the Home folder. Though can't be sure they are being set up correctly there.

In the same menu trying to open "Desktop" gets me a c[/FONT][/SIZE][SIZE=2][FONT=Courier New]an't open eye of Gnome dialogue:[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]
Eye of Gnome Image Viewer      No images found in the 'file///home/myname/desktop'. 

Where can I get a utilities disc for Linux or preferably for Ubuntu 10.10?

MTIA.

Mike.


 [/FONT][/SIZE]

a littlle confusing ?

there is no registry in linux, registry is a windows thing.

and what do you mean by a utilities disc for linux ? and Ubuntu whatever the version is Linux.....the kernel is linux, all the bells and whistles on top is the GNU and whatever distro such as Ubuntu

image viewer is for vieiwing images ? is that what you are trying to do ? or you mean browse the files in Home directory ? nautilus is your file browser, image viewer will give you an error about no images if none are there ?

---

### Post by Azdour on 2011-06-24
Hi,

It looks like the folders 'open with' function has been replaced by Image Viewer. Does the following topic help?:

[http://ubuntuforums.org/showthread.php?t=1710048](http://ubuntuforums.org/showthread.php?t=1710048)

---

### Post by haqking on 2011-06-24
<spamlink>


LOL wrong thread ?

did you have a point ? ;-)

---

### Post by Dangertux on 2011-06-24
This tutorial should get you where you want to be.

[http://www.johannes-eva.net/change-the-default-application-ubuntu-linux](http://www.johannes-eva.net/change-the-default-application-ubuntu-linux)

---

### Post by oldos2er on 2011-06-24
Right-click on any folder  (if none available on Desktop, create one), Open With, Other Application, scroll down and choose 'Open Folder'.

What kind of utilities are you looking for?

---

### Post by Weatherlawyer on 2011-06-30
Thanks all fror replying.
 
I am not aware of the intricacies of Linux and am still making the crossing. In my case the quite crossing.
 
Adour is correct in summation. One or two file endings have been change but opening the "Computer" file manager allows me to inspect the whatever Ubuntu registry is called.
 
But how would it have managed to change it?
(The hard drive was the slave to another HDD which housed Ubuntu UE. That one won't open though I believe the documents on it are intact. No idea what went wrong though they were both instelled as master drives separately.)
 
I will d/l the two links for digestion at home.
 
"What kind of utilities are you looking for?"
Dare I say: "Registry utils?"
 
Is there a restore button files like wot are hidded?
Thanks again, all .

---

### Post by Weatherlawyer on 2011-06-30
> **Dangertux said:**
> This tutorial should get you where you want to be.
 
[http://www.johannes-eva.net/change-the-default-application-ubuntu-linux](http://www.johannes-eva.net/change-the-default-application-ubuntu-linux)
 
Looks favourite.
 
I love gedit and would like to use it in place of Writer if only it did line spacing and page background.

---

### Post by haqking on 2011-06-30
> **Weatherlawyer said:**
> Thanks all fror replying.
 
I am not aware of the intricacies of Linux and am still making the crossing. In my case the quite crossing.
 
Adour is correct in summation. One or two file endings have been change but opening the "Computer" file manager allows me to inspect the whatever Ubuntu registry is called.
 
But how would it have managed to change it?
(The hard drive was the slave to another HDD which housed Ubuntu UE. That one won't open though I believe the documents on it are intact. No idea what went wrong though they were both instelled as master drives separately.)
 
I will d/l the two links for digestion at home.
 
"What kind of utilities are you looking for?"
Dare I say: "Registry utils?"
 
Is there a restore button files like wot are hidded?
Thanks again, all .


This is Linux not windows, Linux does not have a registry.

A registry is a heirarchical DB for configuration information pertaining to the operating system, its hardware and software installatioins.

and would be reached using regedt or regedt32 in a Windows based OS.

the closest thing to regedt or regedt32 in in lInux would be gconf-editor.

in Linux configuration information is stored in text files which you can edit if you need to.

I think you are referring to the file system and its directory structure in which case you would use terminal or your GUI of choice which usually in Ubuntu would be nautilus.

what registry utils do you mean, what do you need to do in Linux for which you need these so called registry utils ?

and are you asking how to unhide or view hidden files ?

---

### Post by sandman887 on 2011-06-30
> there is no registry in linux, registry is a windows thing.

I wonder if he was talking about gconf-editor. I can see how people might mistake that as a registry.

---

### Post by ptminh20 on 2011-06-30
lol, I am skeptical when read thread's name, so strange, i have never heard it before. does linux have registry.reg? I think threader was confused between linux and windows. 
many people takes this mistake in first short time to use linux.

---

### Post by haqking on 2011-06-30
> **sandman887 said:**
> I wonder if he was talking about gconf-editor. I can see how people might mistake that as a registry.


yeah i mentioned Gconf editor in my post.

I am pretty sure he is confused thats all

---

### Post by sandman887 on 2011-07-01
Oh, you're right. I missed that line :P

---

