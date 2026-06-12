---
title: "Computer asking me which system do I want"
date: 2012-04-08
forum: General Help
---

### Post by L.E.n on 2012-04-08
Hello, I've got a last question for today I guess.
I've installed Ubuntu 10.10 today and right after that, Windows 7 (onto another partition, of course), though when I turn on the computer, the Windows is automatically booting without even asking me which system would I like to use.
Is there any way how to fix that? So the computer will always ask me which system do I want to use?

Thanks in advance.

---

### Post by bpb101 on 2012-04-08
It should ask you. 
What the pc ?

---

### Post by Caltac on 2012-04-08
Have you installed rEFIt?

---

### Post by raja.genupula on 2012-04-08
But one thing , Ubuntu 10.10 will be EOL by this month . you better to have a upgrade to newer versions or make a fresh install of new version .

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

EDIT: Now i read it clearly , you need to reinstall the GRUB . look at grub recovery in my signature .  

All the best .

---

### Post by raja.genupula on 2012-04-08
> **Caltac said:**
> Have you installed rEFIt?

Grub can handle this situation my friend :) .

---

### Post by na5h on 2012-04-08
You need to restore the Ubuntu GRUB bootloader. Please have a look at this thread: 
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")
You can also simply re-install Ubuntu.

It is recommended that you install Windows BEFORE you install Ubuntu, as the Windows installation will write over the bootloader.

---

### Post by dylan07 on 2012-04-08
[FONT=Arial][SIZE=2][COLOR=Black][http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Go there, scroll halfway down, to: **"**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Adding Ubuntu to the Windows Bootloader[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]"

EDIT: I did not relize there was a similar post above mine. But mine is an easier method, with a GUI that you use in Windows. I would recomend my method first, as it is easier. And has a GUI.
[/COLOR][/SIZE][/FONT]

---

### Post by dniMretsaM on 2012-04-08
> **dylan07 said:**
> [FONT=Arial][SIZE=2][COLOR=Black][http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Go there, scroll halfway down, to: **"**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Adding Ubuntu to the Windows Bootloader[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]"

EDIT: I did not relize there was a similar post above mine. But mine is an easier method, with a GUI that you use in Windows. I would recomend my method first, as it is easier. And has a GUI.
[/COLOR][/SIZE][/FONT]

I would not really recommend this. If something goes wrong, you'll get little or no help from this forum. If something goes wrong with GRUB, you'll have lots of people ready to help. And the fact that GRUB doesn't have a GUI isn't really a big deal. It's just a menu that you navigate with the up and down arrow keys. Not too difficult. I think you're best bet is to install GRUB. As was mentioned earlier, you might just want to update you Ubuntu installation as 10.10 is reaching EOL. That will automatically install GRUB for you (and it will find your Widows partition automatically. GRUB plays nice with other operating systems, unlike some bootloaders I could mention).

---

### Post by ajgreeny on 2012-04-08
> **dniMretsaM said:**
> I would not really recommend this. If something goes wrong, you'll get little or no help from this forum. If something goes wrong with GRUB, you'll have lots of people ready to help. And the fact that GRUB doesn't have a GUI isn't really a big deal. It's just a menu that you navigate with the up and down arrow keys. Not too difficult. I think you're best bet is to install GRUB. As was mentioned earlier, you might just want to update you Ubuntu installation as 10.10 is reaching EOL. That will automatically install GRUB for you (and it will find your Widows partition automatically. GRUB plays nice with other operating systems, unlike some bootloaders I could mention).
+1.

I would strongly agree with this post. Grub is much easier to deal with than the windows bootloader, and copying one or two commands is hardly going to tax anyone who is able to install Ubuntu in the first place. Grub is also updated more easily with the single command ```
sudo update-grub
``` Done!

That wasn't too difficult, was it?

---

### Post by L.E.n on 2012-04-08
> **dylan07 said:**
> [FONT=Arial][SIZE=2][COLOR=Black][http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Go there, scroll halfway down, to: **"**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Adding Ubuntu to the Windows Bootloader[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]"

EDIT: I did not relize there was a similar post above mine. But mine is an easier method, with a GUI that you use in Windows. I would recomend my method first, as it is easier. And has a GUI.
[/COLOR][/SIZE][/FONT]
Works like a charm, thanks a lot.

> **ajgreeny said:**
> +1.

I would strongly agree with this post. Grub is much easier to deal with than the windows bootloader, and copying one or two commands is hardly going to tax anyone who is able to install Ubuntu in the first place. Grub is also updated more easily with the single command ```
sudo update-grub
``` Done!

That wasn't too difficult, was it?
How do you expect me to use that command when I can't even access Ubuntu?
Well, I couldn't, I used that BCD shizzle and it works cool.

Thanks for help guys!

---

### Post by dylan07 on 2012-04-08
So happy i was able to help you! honestly, I have had to do exactly that from experience.
Though, in the future, it is best to install windows first.

Since you where able to fix it, please mark the forum as solved.

---

### Post by dniMretsaM on 2012-04-08
> **L.E.n said:**
> How do you expect me to use that command when I can't even access Ubuntu?
Well, I couldn't, I used that BCD shizzle and it works cool.

Thanks for help guys!

He was talking about updating it after you reinstall GRUB (which I still strongly recommend doing).

---

### Post by dylan07 on 2012-04-08
I am not sure how you got that.He quoted my solution, and talked about using BCD to fix his issue. I gave him instuctions on how to use BCD to fix his issue. Anyways, I am very happy he got it working, either way.

---

### Post by dniMretsaM on 2012-04-08
> **dylan07 said:**
> I am not sure how you got that.He quoted my solution, and talked about using BCD to fix his issue. I gave him instuctions on how to use BCD to fix his issue. Anyways, I am very happy he got it working, either way.

I was talking about L.E.n's response to ajgreeny. I edited my post to clear things up. And yes, it's good that he got it working.

---

### Post by dylan07 on 2012-04-08
> **dniMretsaM said:**
> I was talking about L.E.n's response to ajgreeny. I edited my post to clear things up. And yes, it's good that he got it working.

Yes, I agree with you! He should update after he gets grub back.

---

