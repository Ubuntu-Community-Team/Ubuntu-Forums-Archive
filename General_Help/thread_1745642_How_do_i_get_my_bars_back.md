---
title: "How do i get my bars back"
date: 2011-05-01
forum: General Help
---

### Post by the_jlx on 2011-05-01
So who ever decided on unity should be banned from computers for ever.
first takes ages to find things second i have to manually install nvidia drivers then my games still dont work....
i decide i just install compiz settings manager and disable unity plugin.....
Well i have a pretty desktop no shortcuts no bars no menus no nothing...
and all i can do is use a live usb.

---

### Post by the_jlx on 2011-05-01
or a way to go back to last version of ubuntu keeping files would be nice

---

### Post by Sico2 on 2011-05-01
Agreed, I had many little things that I could control and loved them so much on my 10.x  Ubuntu. A CPU core temp for example, show desktop etc. No task bar, no applications. And what makes me crazy is the window closing/minimasing buttons on the left hand side with borders disappearing altogether! Who does that? Also the vertical scrolling bar on the windows... it's impossible to use it.
Just burned 10.04 LTS back on my cd and will erase this unity-based Gnome mix whatever it is supposed to be.

I also can't imagine how want the developers to keep distributing this unity-based system after so many posts with flaws and incompatibility on the forum. Disgrace. [-X

---

### Post by mwl128340 on 2011-05-01
I agree with the unity comments you guys made. i tried it and did not like it at all. there is a way to use gnome wth 11.04. on the login screen, the bottom has a dropbox and you can choose to log into ubuntu classic. that is the gnome desktop.

---

### Post by Spr0k3t on 2011-05-01
If you are trying to find the Login Screen from inside Unity, you can do this:

Alt + F2; gdmsetup

Then change the default session to "Ubuntu Classic"

---

### Post by Yayestechlab on 2011-05-01
You can either fix unity or use GNOME (The 10.10 desktop). 


Here are step by step instructions:
1. Reboot. 
2. Click your user name.
3. At the bottom of the screen click the sessions menu (where it says Ubuntu).
4. Chose Ubuntu classic.
5. Type your password and login.

Here you have two options.

Option 1: Use GNOME as default  
6. Go to System -> Administration -> Login Screen. 
7.Unlock.
8.Chose Ubuntu classic.
9.Click close.

Option 2: Fix unity
6.Open Compiz settings manager
7.Enable the unity plugin
8.Close
9.Restart

As for a reinstall only do it if nothing else works.

---

### Post by the_jlx on 2011-05-07
i finally figuerd out how to get my stuff back
Right click desktop create new file.
edit with txt editor
```
gdmsetup
```
save file.
right click again properties--->permissions--->allow executing.
run file and voila i can get the login screen back

---

### Post by the_jlx on 2011-05-07
> **Spr0k3t said:**
> If you are trying to find the Login Screen from inside Unity, you can do this:

Alt + F2; gdmsetup

Then change the default session to "Ubuntu Classic"


Will give you error screen not found

---

### Post by Spr0k3t on 2011-05-08
> **the_jlx said:**
> Will give you error screen not found

Wow... that is one messed up install.

---

