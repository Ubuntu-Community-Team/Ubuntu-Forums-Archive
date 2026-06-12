---
title: "Ibus related problem"
date: 2010-04-29
forum: General Help
---

### Post by hihihi100 on 2010-04-29
Hi there:

when I click on the Ibus icon, I always get a message:

```
IBus daemon is not started. Do you want to start it now?
```

I click yes, and I get:

```
IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
```

I have no idea how to add the amentioned lines to the amentioned file, I guess its via terminal, but I dont know what do I have to type

Tips please

---

### Post by vamped on 2010-05-11
Are you saying you don't know how to enter text into an editor? Really? Almost any editor will do. Try: Application > Accessories > Text editor.
Files beginning with a dot are hidden. To open your .bashrc file in the text editor, Open > (press control h to display hidden files) and select your file.

Btw, you shouldn't have to put those lines in your bashrc -- it just says you *might* need to. Instead,

System > Administration > Language Support > Keyboard input method system > ibus

That should make it automatic at boot.

p.s. this information is already in the forum. you should search before asking.

---

