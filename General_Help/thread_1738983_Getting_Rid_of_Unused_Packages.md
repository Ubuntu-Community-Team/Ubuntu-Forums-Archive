---
title: "Getting Rid of Unused Packages"
date: 2011-04-25
forum: General Help
---

### Post by fpgdu on 2011-04-25
I have Ubuntu Meerkat (10.10) running on an Inspiron E1505. I have it setup for dual boot with Vista. I installed Kubuntu on top of Ubuntu and now have a blue Kubuntu system loading screen where it used to be purple.

I've installed a lot of programs, most unnecessarily, so I'd now like to get rid of ALL of the unnecessary programs and associated packages or dependencies. I'd also like to get rid of KDE, and any Ubuntu packages I never use.

Is there a quick and relatively easy way to do this?

---

### Post by wolfen69 on 2011-04-25
Boot into your ubuntu install and open synaptic package manager and search for kubuntu-desktop and select *completely remove*. Do the same thing for any other stuff you want removed. Then do:

```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by fpgdu on 2011-04-25
> **wolfen69 said:**
> Boot into your ubuntu install and open synaptic package manager and search for kubuntu-desktop and select *completely remove*. Do the same thing for any other stuff you want removed. Then do:

```
sudo apt-get clean && sudo apt-get autoremove
```


Thanks. There's a lot of KDE stuff left after I do that. Should I just remove everything that comes up on a search in Synaptic Package Manager of "KDE"?

---

### Post by wolfen69 on 2011-04-25
> **fpgdu said:**
> Thanks. There's a lot of KDE stuff left after I do that. Should I just remove everything that comes up on a search in Synaptic Package Manager of "KDE"?

No, I would leave them. The command I gave you should remove any unused dependencies.

---

### Post by bodhi.zazen on 2011-04-25
> **fpgdu said:**
> I have Ubuntu Meerkat (10.10) running on an Inspiron E1505. I have it setup for dual boot with Vista. I installed Kubuntu on top of Ubuntu and now have a blue Kubuntu system loading screen where it used to be purple.

I've installed a lot of programs, most unnecessarily, so I'd now like to get rid of ALL of the unnecessary programs and associated packages or dependencies. I'd also like to get rid of KDE, and any Ubuntu packages I never use.

Is there a quick and relatively easy way to do this?

The easiest method is to perform a minimal install and add only those applications you use.

So add gnome rather then ubuntu-desktop
xfce rather then xubuntu-desktop
kde rather then kubuntu-desktop

You might also like alternate window managers, Openbox, Fluxbox, awesome, ...

If you wish to try to purge, try these commands:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You would need to manually review any config files in your home directory.

---

### Post by fpgdu on 2011-04-25
Don't you miss a lot of critical packages and drivers that way?

> **bodhi.zazen said:**
> The easiest method is to perform a minimal install and add only those applications you use.

So add gnome rather then ubuntu-desktop
xfce rather then xubuntu-desktop
kde rather then kubuntu-desktop

You might also like alternate window managers, Openbox, Fluxbox, awesome, ...

If you wish to try to purge, try these commands:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You would need to manually review any config files in your home directory.

---

### Post by bodhi.zazen on 2011-04-25
> **fpgdu said:**
> Don't you miss a lot of critical packages and drivers that way?

What way ? With a minimal install ?

Not at all, critical packages (kernel for example) are part of the minimal base. Other packages are dependencies or recommends.

You may find you wish to install some extras, such as additional fonts or sometimes additional icon sets.

---

### Post by oldos2er on 2011-04-25
> **fpgdu said:**
> Thanks. There's a lot of KDE stuff left after I do that. Should I just remove everything that comes up on a search in Synaptic Package Manager of "KDE"?

To remove everything KDE, see [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

