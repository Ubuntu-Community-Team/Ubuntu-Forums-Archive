---
title: "Got 9.10 now zsnes is missing from its repositories."
date: 2009-11-01
forum: General Help
---

### Post by jord_101 on 2009-11-01
I put 9.10 on a separate part of my hard drive so i currently have 9.04, 9.10 and windows on my computer. 

In 9.04 in the S.P.M it can find and download install both zsnes(emulator) and xshodo(calligraphy) but i cant even find them in 9.10 repositories... Im pretty sure all repositories have been enabled just curious where these have gone. 9.04 can still access them.

Also the new ubuntu software center would be great- if it worked... im behind a proxy so it wont work well i think thats the reason... however SPM works so...yeah.

Any way software centre is a lot easyer to use and to browse for new programs, intalling/downloading is the hard part.

Anyway i want my zsnes back...

---

### Post by Hyporeal on 2009-11-01
Zsnes is in the universe repository. Make sure you have it enabled in System->Administration->Software Sources and push the "Reload" button in Synaptic.

Xshodo does not appear to be in the repositories in 9.10. Does it have a project website from which you might download a .deb file?

---

### Post by jord_101 on 2009-11-01
Yep i have that enabled and done that... doesnt work

xshodo does have a site to download it from same with zsnes and flash(all 3 i have been trying to install by not using SPM) but for the life of me i dont no how to install programs that arnt in synaptic on linux. 

Im curious y ubuntu isnt like windows it is very inconvenient not to be able to install a package by merely clicking on it. I know ubuntu is supposed to be differnt and it is in many good ways but y make this so hard. 

Software centre can find zsnes but not xshodo, however the zsnes page is missing an install button but anyway as i said behind a proxy and software center doesnt seem to work behind it.

---

### Post by Hyporeal on 2009-11-01
Regarding Zsnes:

It sounds like you're having trouble with your download server. Have you tried changing the server in Software Sources? Choose the "Main server" if it's not already selected.

Regarding Xshodo:

There are a few ways to install software that is not in the Ubuntu repositories. The easiest is to download the package as a .deb file and run it. Unfortunately, not all software comes nicely packaged in a .deb file so you might be stuck with a more complex installation mechanism.

I think I found the Xshodo website, but the download link appears to be broken. I'm not sure what's going on there.

---

### Post by jord_101 on 2009-11-02
I think my friend came up with the problem im running a 64bit system and he thinks therefore it will not work cause all other settings r fine

---

### Post by TremerePuck on 2010-01-03
I have the exact same problem. Had to find a deb and install manually.

---

