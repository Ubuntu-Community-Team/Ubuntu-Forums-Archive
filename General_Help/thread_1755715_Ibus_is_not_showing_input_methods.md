---
title: "Ibus is not showing input methods"
date: 2011-05-11
forum: General Help
---

### Post by apurbapaul0 on 2011-05-11
Hi all,
I have just installed ubuntu 11.04. Now I have installed, from the language support, the bengali language. And now select input method as ibus. Now when I am going to ibus preference to select input method, it is not showing any language, except chinese, which was installed by default. I don't know what to do now. :confused:  Please help me. Thanks in advance. 

I am using ubuntu 11.04X64 bit version

---

### Post by luisfhg on 2011-06-09
HI.
i'm using Ubuntu 11.04 (32 bits) and i have the same trouble :(, i try installing the language (russian) on the language support but the checkbox "input methods" is greyed :confused:

Thanks in advance.

---

### Post by apurbapaul0 on 2011-06-09
> **luisfhg said:**
> HI.
i'm using Ubuntu 11.04 (32 bits) and i have the same trouble :(, i try installing the language (russian) on the language support but the checkbox "input methods" is greyed :confused:

Thanks in advance.

Hi luisfhg
I have found some solution from the [Linux User Group @ IIT Delhi]("https://groups.google.com/forum/#%21topic/iitdlug/wXP0gm9cQTY"). Just install [FONT=Helvetica]ibus-m17n, using this command
[/FONT]```
[FONT=Helvetica]sudo apt-get install ibus-m17n [/FONT]
```[FONT=Helvetica]
And then you should see all the option you have enabled the language from language support. You can check it in
[http://apurbapaul.blogspot.com/](http://apurbapaul.blogspot.com/)
[https://groups.google.com/forum/#!topic/iitdlug/wXP0gm9cQTY]("https://groups.google.com/forum/#%21topic/iitdlug/wXP0gm9cQTY")

Hope this will work. :)

[/FONT]

---

