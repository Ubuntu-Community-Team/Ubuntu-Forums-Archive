---
title: "How do I add text on booting before login on ubuntu server?"
date: 2009-07-07
forum: General Help
---

### Post by jm8254og on 2009-07-07
I am sorry for my ignorance on this subject.  I do not know what I am looking to do is called exactly. I basically want to add my own text to the boot process ie, instructions.  I am using Ubuntu 8.10 server with no desktop installed.  

An example of what i am talking about is on security distros such as backtrack where you boot to console and instructions to "type startx" are given.  kinda like a textual post splash screen? If nothing else I just need to know what that is called so I can search more.


Thanks

Oh I am planning on using remastersys to make this a live cd as well if that matters.

---

### Post by danwood76 on 2009-07-07
I'm not quite sure what you want to do. Do you want a message before or after you login?

A login script might be what you are after if you are thinking after login.

---

### Post by jm8254og on 2009-07-07
I guess I could try that.  So that leads me to this.  When you log into ubuntu server you get a message that says:

"The programs included with the Ubuntu system are free.....

Ubuntu comes with ABSOLUTELY NO  WARR....", ect

I assume this is a simple script running.  Anyone know where it is located?  This happens after login but that is ok for what I am doing.

---

### Post by matth@intermetamucil.com on 2009-07-07
```
# /etc/motd
```

---

### Post by jm8254og on 2009-07-07
Awesome!! thanks.

---

