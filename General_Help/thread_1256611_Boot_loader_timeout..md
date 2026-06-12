---
title: "Boot loader timeout."
date: 2009-09-02
forum: General Help
---

### Post by Vinu Raj V on 2009-09-02
Hai, everyone. I use Windows along with ubuntu. Please help me to increase the timeout in boot loader?

---

### Post by drs305 on 2009-09-02
Assuming you have Grub Legacy and not Grub 2, it's an easy edit of /boot/grub/menu.lst but I still recommend StartUp-Manager. It's a gui app that lets you tweak lots of grub settings. See "SUM" link in my signature line.

If you prefer to edit it manually, edit /boot/grub/menu.lst and change "timeout 10" to whatever value in seconds you wish.
```

gksudo gedit /boot/grub/menu.lst

```

If you aren't seeing the menu at all, place a # symbol in front of "hiddenmenu". Again, SUM can do it for you.

---

### Post by Vinu Raj V on 2009-09-02
Thank you drs305 for the reply. As i am new to ubuntu or i can say 'new to linux', you guys are my help. Well, that was my first post.

---

### Post by drs305 on 2009-09-02
> **Vinu Raj V said:**
> Thank you drs305 for the reply. As i am new to ubuntu or i can say 'new to linux', you guys are my help. Well, that was my first post.

I didn't notice it was your first post. Welcome to Ubuntu Vinu Raj V and to the Ubuntu forums.

I guess while I am here, I will tell you about the "Solved" feature. Once you have your problem fixed, it is helpful if you marked the thread "Solved". You do this by clicking on the "Thread Tools" link near the top right of the original post.

Marking a thread solved allows helpers concentrate on posts that still need to be addressed.

Again, welcome.

---

