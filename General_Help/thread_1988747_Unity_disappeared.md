---
title: "Unity disappeared"
date: 2012-05-28
forum: General Help
---

### Post by Starwolf on 2012-05-28
Well, this is really wierd.

My system ran normally until about 1 hour ago. I did a reboot, and from then on, Unity was gone. I have my desktop Icons, but no launcher, no panel, no window controls.

I tried "unity --reset" in the terminal, but this just crashes. Logging in as "Guest" doesn't help either.

Since I'm not exactly an expert on ubuntu, I have no idea how to access system settings...
And this is bad, because I have lot of work left to do... :(

---

### Post by maverickaddicted on 2012-05-28
See this - 

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html]("http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html")

---

### Post by Starwolf on 2012-05-28
Thanks for the quick reply:KS

But it doesn't help

The terminal accepts the commands from the link without giving any output at all, then the "unity --reset" command doesn't accomplish anything.

---

### Post by maverickaddicted on 2012-05-28
> **Starwolf said:**
> Thanks for the quick reply:KS

But it doesn't help

The terminal accepts the commands from the link without giving any output at all, then the "unity --reset" command doesn't accomplish anything.

After running following commands in this order -

```

gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

```
```

rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
rm -rf ~/.config/compiz-1/compizconfig/*

```
```

unity --reset

```

Try to restart unity using this command -

```
unity
```

You can also try -

```
compiz --replace
```

If it still doesn't work try to re-install the Ubuntu destkop from TTY terminal using this command -

```
sudo apt-get install --reinstall ubuntu-desktop
```


If nothing works, then this guide has everything about unity and compiz, you want to try out.

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by Starwolf on 2012-05-28
Should it happen again, I'll try this out. In the meantime, I lost patience and  reinstalled the system during my lunch break... Maybe I should be more patient in the future... ](*,)

But anyway - thanks again for the quick response. :)

---

