---
title: "office 2007"
date: 2009-10-08
forum: General Help
---

### Post by waltwin on 2009-10-08
I have installed MS office 2007 in ubuntu 9.04 and it seems to work well. The problem I am having is that the fonts are not very sharp. Any ideas would be appreciated.

waltin

---

### Post by scorp123 on 2009-10-08
> **waltwin said:**
> The problem I am having is that the fonts are not very sharp. Any ideas would be appreciated. Winetricks

Get it from here:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Or directly execute this command:
```
wget http://www.kegel.com/wine/winetricks
```

So "winetricks" is a program, so to work it needs to be executable. For that reason you'd execute this command:
```
chmod 755 winetricks
```

Once that is done you can launch it from the shell -- and before that you did close all "wine" applications, yes?
```
./winetricks
```

I'd suggest you pick these options:
- sandbox
- fontsmoothing-rgb
- all fonts

You'll see winetricks download a few things for you .... after it's done you can launch your Windows programs again .... and taadaaaa ... they should look far nicer now.

---

### Post by waltwin on 2009-10-12
> **scorp123 said:**
> Winetricks

Get it from here:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Or directly execute this command:
```
wget http://www.kegel.com/wine/winetricks
```

So "winetricks" is a program, so to work it needs to be executable. For that reason you'd execute this command:
```
chmod 755 winetricks
```

Once that is done you can launch it from the shell -- and before that you did close all "wine" applications, yes?
```
./winetricks
```

I'd suggest you pick these options:
- sandbox
- fontsmoothing-rgb
- all fonts

You'll see winetricks download a few things for you .... after it's done you can launch your Windows programs again .... and taadaaaa ... they should look far nicer now.
Your response has corrected my problem. I must first apologise for not thanking you much earlier. I am not a rude person but in this case just ignorant in the ways of ubuntu and how to communicate. I hope that you receive this reply and will accept my apology. 

waltwin

---

