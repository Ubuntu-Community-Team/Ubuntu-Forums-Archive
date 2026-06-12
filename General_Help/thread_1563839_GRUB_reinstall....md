---
title: "GRUB reinstall..."
date: 2010-08-29
forum: General Help
---

### Post by [::AP::] on 2010-08-29
Greetings - 

I am fairly new to Ubuntu, so please bear with me. I do love it, however. (Lucid Lynx)

Well, I bit off more than I could chew, I already know that...

I was trying to install GFX Grub. Notice, *trying*. Yes, a bit stupid for a beginner. 

So I had to uninstall Grub, and install the new one. Etc... There are guides on the internet (Google "GFX Grub"), and they are all about the same. I made a mistake somewhere, rebooted, and...

Oops. 

Now I have no bootloader! Yay! (Sarcasm)
I have tried using the 9.10 LiveCD that I have (will this work for 10.04?). I do what is suggested, found on forums...

Open terminal...

```
sudo grub
```

This opens a GRUB menu

```
find /boot/grub/stage1
```

My output is (hd0,5)Then...

```
root (hd0,5)
```

Then...

```
setup (hd0)
```

From what I have read you can also use...

```
setup (hd0,5)
```

But it doesn't matter. Then...

```
quit
```

However, this doesn't do squat. :(

------------------------------------

I have also tried Super Grub Disk. 

Once it "fixed" my GRUB, it basically just showed what terminal shows after typing

```
sudo grub
```

You can type stuff, so that may be good. I tried using the terminal grub commands, but to no avail. "/e2fs" files fail to load or something.

I was able to boot into Windows XP from Super Grub Disk, so that is good. If need be, I can install GRUB in Windows, but from my understanding it is better to have it in Ubuntu.

Thanks for reading, and please be kind.

[::AP::]

---

### Post by [::AP::] on 2010-08-29
If need be, I can post pictures tomorrow, if this would help in the explanation. I tried to describe it as best I could.

---

### Post by jimbop99 on 2010-08-29
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I point a lot of people here. It worked for me.

---

### Post by oldfred on 2010-08-29
Unless you upgraded and kept grub legacy you have grub2. The instructions you posted are for grub legacy.

jimbop99's instructions for installing grub2 to the MBR will work just fine. 

If you somehow installed grub legacy into your system, you may have issues as they often do not work well if both are installed. If the grub2 update to the MBR does not work we may have to uninstall both grub & grub2 and reinstall grub2.

---

### Post by [::AP::] on 2010-08-29
Eh... I will try? I am still slightly confused, but thank you for your guidance. 

Also, thanks for responding so quickly. One of the reasons I chose Ubuntu was the great community. :D

---

### Post by oldfred on 2010-08-29
If you want specific commands to run post this which you can run from liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by [::AP::] on 2010-08-29
Yay! I got it... Thank you VERY MUCH. I required several tries (don't ask), but it works. 

However, I think I installed Grub2 on /dev/sda6, and thats Ubuntu partition, not MBR.:confused: 

*I think, then again, I am a newbie.:redface:   

But it works, so I am happy, for now. 

Thanks again!

(Oh, should I make this thread "solved"?)

[::AP::]

---

### Post by [::AP::] on 2010-08-30
Installed BURG, it looks nice now...:D

---

