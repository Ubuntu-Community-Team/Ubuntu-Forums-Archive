---
title: "Can't get Super Key working in Compiz"
date: 2011-04-28
forum: General Help
---

### Post by Giraffro on 2011-04-28
I've just upgraded to 11.04 and I can't get Super Key working in Compiz, which should be binded to Left Win. It shows up as Multi_key when I enter a key combination. However, if I bind Caps Lock to Super Key it works when entering a key combination. I'm also using a Logitech MK520 keyboard.

Can anyone help?

---

### Post by Hedgehog1 on 2011-04-28
The SUPER key has a new meaning in Unity. Please see the second post in this thread: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by Giraffro on 2011-04-28
This is what I can't get working. Why would it show up as Multikey? Is it because of multiple bindings? I have all the default options in the Keyboard settings so I don't think there should be.

---

### Post by Artiom.Fiodorov on 2011-04-28
My Windows Key shows up as Multi Key in Keyboard binding. Want to use Unity shortcuts but I can not as a result. How to fix it?

---

### Post by misetusame on 2011-04-29
Similar here: none of the Super key shortcuts do anything for me in Unity.

I don't know if I even have Compiz installed or not :neutral:

---

### Post by Hedgehog1 on 2011-04-29
Unity uses Compiz - if you are seeing Unity, you have Compiz loaded.


***The Hedge***

:KS

---

### Post by misetusame on 2011-04-29
> **Hedgehog1 said:**
> Unity uses Compiz - if you are seeing Unity, you have Compiz loaded.

Thanks Hedgey, good to know :)

---

### Post by Artiom.Fiodorov on 2011-04-29
Anyone knows how to map multi key into super? Missing the shortcuts badly...

---

### Post by misetusame on 2011-05-03
I got this working, at least for some Super shortcuts.

I installed CompizConfig Manager following the information here:
[http://askubuntu.com/questions/36910/how-to-remap-keyboard-shortcuts-in-unity-launcher](http://askubuntu.com/questions/36910/how-to-remap-keyboard-shortcuts-in-unity-launcher)

I run the CompizConifg. In "Key to show the launcher" it was set to "Super". I clicked on that "Super" button, and chose "Grab key combination". I pressed my Windows/Super key. This showed in the dialog as "Mode_switch". I clicked OK, and now pressing the Windows/Super key shows the Unity launcher.

---

### Post by Artiom.Fiodorov on 2011-05-03
I am trying to remap my Multi_Key to Super_L by running the following command:
[PHP]xmodmap -e "keysym Multi_Key = Super_L"[/PHP]Only to get the error:
[PHP]xmodmap:  commandline:1:  bad keysym target key symbol 'Multi_Key'[/PHP]My Windows Key shows up as Multi_Key if I run xev.
What is going on?

---

### Post by clanlaw on 2011-05-22
> **Giraffro said:**
> I've just upgraded to 11.04 and I can't get Super Key working in Compiz, which should be binded to Left Win. It shows up as Multi_key when I enter a key combination. However, if I bind Caps Lock to Super Key it works when entering a key combination. I'm also using a Logitech MK520 keyboard.

This looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778717](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778717)
Please anyone seeing this go and add yourself to the bug.
It is not a Compiz issue as it is seen with Unity-2D as well as Unity, and U2D does not use Compiz.

---

### Post by erjoalgo on 2011-06-05
Please read my post for a workaround, 
[http://ubuntuforums.org/showthread.php?t=1775670](http://ubuntuforums.org/showthread.php?t=1775670)

---

### Post by clanlaw on 2011-06-05
> **erjoalgo said:**
> Please read my post for a workaround, 
[http://ubuntuforums.org/showthread.php?t=1775670](http://ubuntuforums.org/showthread.php?t=1775670)
That is not a workaround for the problem here.  The problem here is that the left Win key does *not* work as the Super key in Unity or Unity-2D.

A workaround for the problem here is contained in the bug report in post #11 above.

---

