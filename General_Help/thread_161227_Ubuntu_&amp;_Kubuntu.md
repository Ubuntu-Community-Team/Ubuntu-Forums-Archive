---
title: "Ubuntu &amp; Kubuntu"
date: 2006-04-16
forum: General Help
---

### Post by Hoffmann on 2006-04-16
Hello:

By the way, does anyone here have both Ubuntu (with the original Gnome desktop) and Kubuntu installed? Let me make the question in a different way. Is it possible to have both Gnome and KDE installed, and switch between then at will? When I say 'switch', I mean a complete 'switch'. In oder words, when one decides to use Gnome, even the 'Welcome' splash screen is the Gnome one; where if one decides to use KDE the 'Welcome' splash screen will run, etc. So, I am interested in having both desktops installed, and working as if just one at a time were installed. 
With both desktops installed, can I have any kind of problem?

Hoffmann

---

### Post by Ramses de Norre on 2006-04-16
I have both installed, there are totally no conflicts, kde apps will run better in gnome and vice versa (all libs installed).
To be able to choose the login screen you'll need to boot into console only and start gdm or kdm, you can only boot one automaticaly which would be always the same then.

---

### Post by Hoffmann on 2006-04-16
[QUOTE=Ramses de Norre]I have both installed, there are totally no conflicts, kde apps will run better in gnome and vice versa (all libs installed).
To be able to choose the login screen you'll need to boot into console only and start gdm or kdm, you can only boot one automaticaly which would be always the same then.[/QUOTE]

Thanks for replying.
I didn't understand the last part. If I installed Kunbutu, which of the desktops will be starded automatically, Gnome or KDE.  Is not possible to have a kind of section choose, in order to decide which desktop, I would like to automaticaly boot next time?

Hoffmann

---

### Post by Ramses de Norre on 2006-04-16
In the login screen you can choose that by clicking sessions, but you'll start always either gdm (gnome) or kdm (kde) for the login screen. In both your free to choose gnome or kde though.

---

### Post by aysiu on 2006-04-16
[QUOTE=Hoffmann]Thanks for replying.
I didn't understand the last part. If I installed Kunbutu, which of the desktops will be starded automatically, Gnome or KDE.  Is not possible to have a kind of section choose, in order to decide which desktop, I would like to automaticaly boot next time?

Hoffmann[/QUOTE] Yes, you can choose which one, and you can change the default, but only one can have control of the login screen.

---

### Post by Hoffmann on 2006-04-16
[QUOTE=Ramses de Norre]In the login screen you can choose that by clicking sessions, but you'll start always either gdm (gnome) or kdm (kde) for the login screen. In both your free to choose gnome or kde though.[/QUOTE]

So, can I choose which desktop I would like to be the default one for the login screen? Is that correct?

So, according to you, KDE applications work better on Gnome, and vice-versa.  Is that correct? Why?

One more thing: does you think it is worthy (or better) have both of the desktops installed?

Hoffmann

---

### Post by aysiu on 2006-04-16
> **Hoffmann]So, can I choose which desktop I would like to be the default one for the login screen? Is that correct?[/quote] I'm not sure I understand your question.

There are two login (or display) managers--one's KDM, associated with KDE said:**
> 
So, according to you, KDE applications work better on Gnome, and vice-versa.  Is that correct? Why? Who said that? KDE applications always work better in KDE and the same for Gnome applications in Gnome. All applications *work* in both environments, but they may take a little longer to load in their non-native environments.

> 
One more thing: does you think it is worthy (or better) have both of the desktops installed? If you're in a place where you're deciding between the two, you *should* have both installed. When you install KDE, though, be sure to install it with *aptitude*, not *apt-get*. That way, if you later decide you want to uninstall KDE, it's easier to do:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Hoffmann on 2006-04-16
[QUOTE=aysiu]I'm not sure I understand your question.

There are two login (or display) managers--one's KDM, associated with KDE; the other is GDM, associated with Gnome. Only one (KDM or GDM) can be in charge of the login screen.

However, once you decide which one is in charge (KDM or GDM), either can boot to both KDE and Gnome, and either can set KDE or Gnome to be the default desktop environment you log into.

Keep in mind, though, that if you log into Gnome using KDM or log into KDE using GDM, you will not be able to do a point-and-click shutdown from that environment. You will have to log out and then shut down.

 Who said that? KDE applications always work better in KDE and the same for Gnome applications in Gnome. All applications *work* in both environments, but they may take a little longer to load in their non-native environments.

 If you're in a place where you're deciding between the two, you *should* have both installed. When you install KDE, though, be sure to install it with *aptitude*, not *apt-get*. That way, if you later decide you want to uninstall KDE, it's easier to do:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```[/QUOTE]

aysiu:

I am going to install Kubuntu, so.
2 questions: 

(1) I would like to have GDM login (or display) manager in charge. How can I set it as the default manager, so?

(2) What about installing Kubuntu by using Synaptic? Is it a good idea?

Thanks,
Hoffmann

---

### Post by aysiu on 2006-04-16
[QUOTE=Hoffmann]aysiu:

I am going to install Kubuntu, so.
2 questions: 

(1) I would like to have GDM login (or display) manager in charge. How can I set it as the default manager, so?

(2) What about installing Kubuntu by using Synaptic? Is it a good idea?

Thanks,
Hoffmann[/QUOTE] I don't believe Synaptic keeps of track of what dependencies get installed with a package (and, hence, won't uninstall those dependencies when the package is uninstalled). I would use *aptitude* instead.

And, yes, you can keep GDM as the default display manager. When you install KDM (part of the *kubuntu-desktop* metapackage, you'll be prompted as to which you want to have as the default. Just select GDM. You can always change it to KDM later if you want, too.

---

### Post by PriceChild on 2006-04-16
It is possible to just boot to command line, and then use gdm or kdm to launch whichever one you want.... i think? :)

---

### Post by Ramses de Norre on 2006-04-16
>  So, according to you, KDE applications work better on Gnome, and vice-versa. Is that correct? Why?
KDE apps wont work better in gnome then in kde, but if you install kde you've got all the kde libs installed which will make kde apps run more stable on gnome too.

To boot into console: sudo apt-get install sysv-rc-conf && sudo sysv-rc-conf
search the line for gdm (or kdm whatever you use) and disable it for runlevel 2.

---

### Post by Hoffmann on 2006-04-17
[QUOTE=aysiu]I'm not sure I understand your question.

There are two login (or display) managers--one's KDM, associated with KDE; the other is GDM, associated with Gnome. Only one (KDM or GDM) can be in charge of the login screen.

However, once you decide which one is in charge (KDM or GDM), either can boot to both KDE and Gnome, and either can set KDE or Gnome to be the default desktop environment you log into.

Keep in mind, though, that if you log into Gnome using KDM or log into KDE using GDM, you will not be able to do a point-and-click shutdown from that environment. You will have to log out and then shut down.

 Who said that? KDE applications always work better in KDE and the same for Gnome applications in Gnome. All applications *work* in both environments, but they may take a little longer to load in their non-native environments.

 If you're in a place where you're deciding between the two, you *should* have both installed. When you install KDE, though, be sure to install it with *aptitude*, not *apt-get*. That way, if you later decide you want to uninstall KDE, it's easier to do:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```[/QUOTE]

aysiu:

I just installed Kunbutu, by using aptitude. Just in case, if later I decide to uninstall KDE, how is the command for that?

Thanks,
Hoffmann

---

### Post by aysiu on 2006-04-17
[QUOTE=Hoffmann]aysiu:

I just installed Kunbutu, by using aptitude. Just in case, if later I decide to uninstall KDE, how is the command for that?

Thanks,
Hoffmann[/QUOTE] ```
sudo aptitude remove kubuntu-desktop
``` Read more details [here](http://www.ubuntuforums.org/showpost.php?p=659085&postcount=19).

---

### Post by Hoffmann on 2006-04-20
[QUOTE=aysiu]I'm not sure I understand your question.

When you install KDE, though, be sure to install it with *aptitude*, not *apt-get*. That way, if you later decide you want to uninstall KDE, it's easier to do:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```[/QUOTE]

Hi aysiu,

Does this installation/uninstallation process (by using **aptitude**) also works for installing Xubuntu?

Thanks,
Hoffmann

---

### Post by Hoffmann on 2006-04-20
[QUOTE=Hoffmann]Hi aysiu,

Does this installation/uninstallation process (by using **aptitude**) also works for installing Xubuntu?

Thanks,
Hoffmann[/QUOTE]

Hi aysiu,

Please, disconsider my previous post to you. I just realized that you alread answered my question on the othe post.:grin: 
Thanks!
Hoffmann

---

### Post by Hoffmann on 2006-04-20
[QUOTE=aysiu]```
sudo aptitude remove kubuntu-desktop
``` Read more details [here](http://www.ubuntuforums.org/showpost.php?p=659085&postcount=19).[/QUOTE]

Hi aysiu,

Please, disconsider my previous post to you. I just realized that you alread answered my question on the othe post.
Thanks!
Hoffmann

---

### Post by YumaJim on 2006-04-24
I'm currently using KDE with 5.10 and downloaded the GDM desktop. At the end of the GDM install, I was told to edit some file in order to use GDM. I thought the file was /etc/init.d but, that is a directory. Can someone tell me how to activate
GDM so that I can try it?

YumaJim

---

