---
title: "Won't boot"
date: 2010-12-21
forum: General Help
---

### Post by ananda28 on 2010-12-21
I DL ubuntu 10.4.1 desktop i386 and installed. At startup I get the prompt to use windows xp or ubuntu. I choose ubuntu and get a black screen with a flashing dash line and that all. Any help please? Obviously Im new at this Thanks

---

### Post by Quackers on 2010-12-21
Welcome to UF :-)
What graphics card are you using and how much ram do you have?

---

### Post by amsterdamharu on 2010-12-21
If you boot from live CD does it give you a desktop (just boot from cd and select try Ubuntu)?

If you do could you do the following:
press alt + F2 and type "gnome-terminal" no quotes
In the terminal copy and paste the following command (use right mouse button in terminal and select paste).
```
sudo lshw
```
Select all the text in the terminal and copy paste it to this forum.

Thank you.

---

### Post by ananda28 on 2010-12-22
radeon 9200? 512 g ram

---

### Post by ananda28 on 2010-12-22
radeon 9200? 512 g ram ive tried reDL with wubi too

---

### Post by Quackers on 2010-12-22
Is the screen where you can choose XP or Ubuntu a grub menu (black screen with white OS choice), with the top item highlighted?

---

### Post by ananda28 on 2010-12-22
> **amsterdamharu said:**
> If you boot from live CD does it give you a desktop (just boot from cd and select try Ubuntu)?

If you do could you do the following:
press alt + F2 and type "gnome-terminal" no quotes
In the terminal copy and paste the following command (use right mouse button in terminal and select paste).
```
sudo lshw
```Select all the text in the terminal and copy paste it to this forum.

Thank you.
no cd, just straight up DL

---

### Post by Quackers on 2010-12-22
Have you installed Ubuntu in its own partition or via wubi?

---

### Post by ananda28 on 2010-12-22
ive tried wubi and full download, it takes like 2 hours and crashes

---

### Post by ananda28 on 2010-12-22
havent tried own partition just followed web instructions

---

### Post by Quackers on 2010-12-22
If you haven't burned an image to a disk or a usb you must be using wubi, I think.

---

### Post by bcbc on 2010-12-23
If you're using Wubi you should see 
"Completing installation. Press ESC for more boot options..."

If you see this press ESC and try some boot options as described here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (there a post specifically for Wubi install customisation).

I have an ATI 9000 with 512MB ram and it boots fine. So not sure what issues you are having. What are the rest of the computer's specs... make/model/ etc.

---

