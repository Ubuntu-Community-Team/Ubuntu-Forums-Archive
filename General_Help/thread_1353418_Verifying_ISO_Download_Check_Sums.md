---
title: "Verifying ISO Download Check Sums"
date: 2009-12-12
forum: General Help
---

### Post by carolina on 2009-12-12
I downloaded a  Ubuntu 9.10 iso via Transmission and have a cd icon on the desktop in which to burn . I do not however understand how to verify check sum before burning . 

Looking in the file system - usr - bin i see the blue icon for Transmission and if i right click that the Transmission app opens but starts an up -load procedure so maybe i accidentally did something to activate .

I have tried the terminal commands based on Linux documentation but get a file directory not found message . Can anyone straighten me out ?   ;)

---

### Post by avtolle on 2009-12-12
```
cd Desktop
md5sum nameof.iso
``` where nameof.iso is the name of the iso file you downloaded. The first command changes the active directory to the Desktop, where the file is.

---

### Post by sisco311 on 2009-12-12
The easiest way to get the exact path to a file/directory in the terminal is to drag the file in the terminal window.

So, type:
```
md5sum
```
type a space, drag the .iso in the terminal and press Enter.

the md5sums of the karmic .isos:
```
836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe
```

---

### Post by carolina on 2009-12-12
> **avtolle said:**
> ```
cd Desktop
md5sum nameof.iso
``` where nameof.iso is the name of the iso file you downloaded. The first command changes the active directory to the Desktop, where the file is.

This is what i did and got :

alan@alan-desktop:~$ cd Desktop
alan@alan-desktop:~/Desktop$ md5sum ubuntu-9.10-alternate-i386.iso
^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^

Does this make sense ?


I take it this a bad download ?

---

### Post by Cheesemill on 2009-12-12
If you downloaded using BitTorrent (which is the case with transmission) then there is no need to check the md5sum, it will be OK. The BitTorrent protocol automatically hash checks the file as part of the download process.

---

### Post by sisco311 on 2009-12-12
> **carolina said:**
> This is what i did and got :

alan@alan-desktop:~$ cd Desktop
alan@alan-desktop:~/Desktop$ md5sum ubuntu-9.10-alternate-i386.iso
^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^

Does this make sense ?


I take it this a bad download ?

That looks weird. Are you holding down some keys?

---

### Post by carolina on 2009-12-12
> **sisco311 said:**
> The easiest way to get the exact path to a file/directory in the terminal is to drag the file in the terminal window.

So, type:
```
md5sum
```type a space, drag the .iso in the terminal and press Enter.

the md5sums of the karmic .isos:
```
836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe
```

After dragging the file into terminal i get a pop up window for the image burning setup . Is that what should happen ?

---

### Post by carolina on 2009-12-12
Yeah did do that ..

---

### Post by carolina on 2009-12-12
> **carolina said:**
> Yeah did do that ..


Anyway , thanks guys for the tips . Next time i will know .  :o

---

