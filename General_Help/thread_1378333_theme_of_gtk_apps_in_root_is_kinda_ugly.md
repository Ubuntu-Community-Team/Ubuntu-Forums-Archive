---
title: "theme of gtk apps in root is kinda ugly"
date: 2010-01-11
forum: General Help
---

### Post by dumblebee100 on 2010-01-11
for your information Im using kubuntu 9.10 and I didn't enabled any user other than myself (I mean I dont have root user enabled )

I want to have same theme for the root apps just like the theme under my session 

the thing I want is explained clearly in screenshot
the root synaptic is ugly and the synaptic from the user(  ofcourse it doesn't have administrative privileges ) is following my kubuntu theme 
I use the kde43-oxygen-molecule gtk theme for my gtk application so that even gtk apps look like kde4 

I did my workaround .
I copied all the theme related things i.e., gtkrc.mine, .gtkrc-2.0-kde4 and kderc but still I get the ugly theme for my root apps

---

### Post by ankspo71 on 2010-01-11
Hi,

I'm not sure about this working in Kubuntu, but if Kubuntu stores the theme files in the same folders and Ubuntu does, then this line of codes should help:

```

sudo ln -s ~/.themes /root/.themes

sudo ln -s ~/.icons /root/.icons

sudo ln -s ~/.fonts /root/.fonts

```
What this does is links your themes folder(s) to the root users themes folder(s) so that the themes automatically match (even if you decide to change your theme later).

It would be best to first browse your Kubuntu system first to make sure the folder locations are correct though, otherwise it might screw something up.
Hope this helps.

---

### Post by dumblebee100 on 2010-01-11
Thanks 
that solved my problem ..now my synaptic is lot better for eyes

---

