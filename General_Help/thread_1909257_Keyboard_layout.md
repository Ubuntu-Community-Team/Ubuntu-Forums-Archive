---
title: "Keyboard layout"
date: 2012-01-14
forum: General Help
---

### Post by Borunco on 2012-01-14
Hi, I don't know whether to make a new thread for this or not, But on my acer aspire one net book. I just installed a clean Lubuntu 11.10 and everything went great, but after doing updates,and setting things the way I like. It all went good and then out of the blue my keyboard will wright like if it's in upper case but just in the keys u,i,o,p,0,j,k,l,m. u=4, i=5,o=6,p=*,j=1, k=2, l=3, m=0, 0=/. I don't know what happen, it did this to me last week also. When I had Lubuntu 11.04 it never did that.
dose any body know what that could be? I'm writing this post from my desktop, because can't time with my net book right now.:(

---

### Post by mörgæs on 2012-01-14
Moved to General Help.

---

### Post by Borunco on 2012-01-14
Thank you

---

### Post by Rodney9 on 2012-01-15
> **Borunco said:**
> Hi, I don't know whether to make a new thread for this or not, But on my acer aspire one net book. I just installed a clean Lubuntu 11.10 and everything went great, but after doing updates,and setting things the way I like. It all went good and then out of the blue my keyboard will wright like if it's in upper case but just in the keys u,i,o,p,0,j,k,l,m. u=4, i=5,o=6,p=*,j=1, k=2, l=3, m=0, 0=/. I don't know what happen, it did this to me last week also. When I had Lubuntu 11.04 it never did that.
dose any body know what that could be? I'm writing this post from my desktop, because can't time with my net book right now.:(

I don't know how it happened, you could use Lxkeymap to test your keyboard.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Borunco on 2012-01-15
Thank you for your reply rodney9,
In response, I have tried the Lxkeymap,checked the settings, I have it on US setting, even when I reset it will not change. I will keep searching, I'm hopping that some one had a similar problem in the past.
Thank you 
borunco

---

### Post by Borunco on 2012-01-15
Just an update, when I go to LXkeymap 1. I can change to any language and it dose not do anything. 2. I have re-install the LXkeymap package and nothing. 3. When I hold the Fn key, I can get the keys to work.
Any thought?

---

### Post by Borunco on 2012-01-16
Hi all, after lots of research. I was able to figure the problem, it seems that after I did (sudo apt-get update && sudo apt-get upgrade) for some reason the computer turn the Num Lock function without me knowing it. I had done the clean install a couple of times and the problem was the same. So the correction is if you have the same problem with this type of net book, look up at the top left corner of the computer, the little lock with the number one on it is the number lock light, if that light is on, then you can turn it off by pressing key Fn+F11 and the light should turn off. Thats it
Thank you all
Borunco:popcorn:

---

### Post by Borunco on 2012-01-22
Hi all, just a correction on the post above. It seems that on my Acer net book you can start/stop The alternate key pad when you press fn+f11. Well what was making it come on at boot was when I install (sudo apt-get install numlockx). I realize that it was still happening at boot so I would have to manually turn it off, so I backed tract all the installs I had done on my new Lubuntu 11.10 install and found the culprit. I had installed that app. on my other computers with no problem, but the others did not have that alternate key pad function. Well I just wanted to share this in case it could help someone in the future.
Than you 
borunco

---

