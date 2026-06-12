---
title: "how to add keyboard shortcut to script"
date: 2010-09-09
forum: General Help
---

### Post by rhythmiccycle on 2010-09-09
I have no problem doing this with Ubuntu, but I started using lubuntu on my netbook, and I like it.

I want to add a keyboard shortcut that runs a shell script (saved to a file). from googleing I found that I can edit keyboard shortcuts from

~/.config/openbox/lubuntu-rc.xml

in this file I can find this type of stuff that I get:

```

<keybind key="C-A-Right">
   <action name="DesktopLeft>
      <dialog>no</dialog>
      <wrap>no</wrap>
   </action>
</keybind>

```

So i guess there is some type of action that can run the script  I wrote, but I don't know the syntax. 

what is the proper syntax?

also, the power button (the psychical one on the netbook) doesn't do any thing when I press it, I want the computer to shutdown when I press it what is the "key" and "action" to do this?

---

