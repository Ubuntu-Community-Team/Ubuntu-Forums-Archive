---
title: "disable auto-opening of nautilus window after auto-mount"
date: 2011-11-14
forum: General Help
---

### Post by CryptKeeper777 on 2011-11-14
When I plug in a USB device, it's mounted automatically. Thats fine. But for every device, a new Nautilus window is opened. That's not so fine, mainly for two reasons: I have several partitions on my USB HD, and for every partition, a window is opened, so I end up with four windows when I only need one (or none because I do lot's of stuff only with the terminal). And, secondly, the windows are opened above all windows, but the previously opened window is still the selected window, so when I want to close the newly opened window with a shortcut, I often accidentally close the old window beneath the new windows which I - of course - usually still needed. 

How can I disable this auto-opening in Ubuntu 10.10? If I remember right, I've found this option in 10.04 myself, but now, after the update, I haven't.

And, by chance, is there a solution for the other mentioned problem that new windows are often opened above all others, but aren't selected? That also happens when I open a PDF, for example, and I've already quite often closed the terminal window I still needed when I actually wanted to close the PDF document I'd just opened to have a short glimpse at. That really sucks.

---

### Post by Blackbug on 2011-11-14
I am sorry I am not answering your problem but asking mine over here..
In my case, its not auto mouting my windows NTFS partition. Initially it was, but now its not auto mounting neither the windows NTFS partitions nor any USB external drive.
Its auto mounting FAT32 partition.
 
I even tried mouting manually but gives some input/output error and sometimes error code 21.
 
Sorry for asking here..but i am facing this problem alot..and couldnt find an answer to it yet

---

### Post by lukeiamyourfather on 2011-11-14
> **Blackbug said:**
> I am sorry I am not answering your problem but asking mine over here..
In my case, its not auto mouting my windows NTFS partition. Initially it was, but now its not auto mounting neither the windows NTFS partitions nor any USB external drive.
Its auto mounting FAT32 partition.
 
I even tried mouting manually but gives some input/output error and sometimes error code 21.
 
Sorry for asking here..but i am facing this problem alot..and couldnt find an answer to it yet

Don't hijack threads. Start a new thread.

For the original poster, see this link if you haven't already.

[https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting](https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting)

I'm not sure about the window focus issue so I'll let somebody else tackle that.

---

### Post by CryptKeeper777 on 2011-11-14
> **lukeiamyourfather said:**
> 
For the original poster, see this link if you haven't already.

[https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting](https://help.ubuntu.com/community/Mount/USB#Configuring_Automounting)

I don't have the options media_automount and media_automount_open for Nautilus in the gconf editor. The latter would be what I'm looking for. And I don't have the category 'media' in the Nautilus preferences window, as described in the link. 

I suppose this site still refers to 10.04, because, as mentioned, I could disable the auto-opening in the Nautilus preferences before I updated to 10.10. But these preferences seem to have been dropped for whatever reason...
> 
I'm not sure about the window focus issue so I'll let somebody else tackle that.It's not a mayor issue, but something I'll eventually get used to (not blindly hitting the close-window-shortcut but making sure the right window will be closed first). I just thought: why not ask once I'm here already...

---

### Post by wowcolombia1 on 2011-11-14
Think about when you didnt have those problems,i am sure that when you installed Ubuntu you didnt have those problems,now think about what you did that caused those problems.If you dont renember you are in a bad luck.If you renember,you can fix what you know that you did to cause that problem.Also think about the day before you started having that problem.If dont renember well i dont know but i can give you that tip that maybe helps you.
Thats all,hope this helped :)

---

### Post by CryptKeeper777 on 2011-11-14
> **wowcolombia1 said:**
> Think about when you didnt have those problems,i am sure that when you installed Ubuntu you didnt have those problems,now think about what you did that caused those problems.If you dont renember you are in a bad luck.If you renember,you can fix what you know that you did to cause that problem.Also think about the day before you started having that problem.If dont renember well i dont know but i can give you that tip that maybe helps you.
Thats all,hope this helped :)
As for the problem with the auto-opening windows, I can exactly tell you what I did: I updated to Ubuntu 11.10! :) I did so rather by accident, BTW, I didn't realize it's such a major update, I think I would've waited a bit if I'd realized it...

As for the other problem: I don't know if it was ever different. But if so, I's also blame the 11.04->11.10 update... Blaming anything else would be impossible because I just switched to Linux this summer and thus installed a lot of stuff since then in a quite short time.

---

