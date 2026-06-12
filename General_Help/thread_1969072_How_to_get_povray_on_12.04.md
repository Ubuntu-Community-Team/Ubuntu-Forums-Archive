---
title: "How to get povray on 12.04"
date: 2012-04-29
forum: General Help
---

### Post by DrKosy on 2012-04-29
I just upgraded my ubuntu to 12.04 and had to recognize that with the new version my povray raytracer is gone. I suppose they droped the support of this package so I ask myself how to get back my lovely povray.

I tried installing the stable Debian package but synaptic told me this will brake my libpng12-0 and won't proceed with the installation.

Are there any raytracers out there who could help me out?

P.S: I run lubuntu on amd64 hardware and therefore installed lubuntu 12.04 for 64-bit systems.

---

### Post by matt_symes on 2012-04-29
Hi

What about using blender instead ?
```

matthew@matthew-Aspire-7540 ~ % apt-cache search ^blender
blender - Very fast and versatile 3D modeller/renderer
blender-dbg - debug symbols for Blender
blender-ogrexml - Blender Exporter for OGRE
matthew@matthew-Aspire-7540 ~ % 
```

I believe you can ray trace on that.
```

matthew@matthew-Aspire-7540 ~ % cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
matthew@matthew-Aspire-7540 ~ %
```

I should be available for 12.04.

Kind regards

---

### Post by Feneric on 2012-04-30
> What about using blender instead ?

Not so much.  Not sure about the situation the original poster is in, but unless Blender has a POV-Ray compatibility mode, it's not going to help for anyone who's got a library of POV-Ray objects.  Usually so far as I know though it goes in the other direction -- that is, there are a fair number of Blender users who use POV-Ray as the rendering engine for their Blender work.

Anyhow, it looks like it's pretty trivial to download the Oneiric packages and manually install them.  For the AMD 64 bit build, the files can be downloaded from:

[LIST]
[*][http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray_3.6.1-12_amd64.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray_3.6.1-12_amd64.deb)
[*][http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-includes_3.6.1-12_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-includes_3.6.1-12_all.deb)
[*][http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-examples_3.6.1-12_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-examples_3.6.1-12_all.deb)
[*][http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-doc_3.6.1-12_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/p/povray/povray-doc_3.6.1-12_all.deb)
[/LIST]

and the direct installs can be installed with commands like:

```
dpkg -i povray_3.6.1-12_amd64.deb
dpkg -i povray-includes_3.6.1-12_all.deb
dpkg -i povray-examples_3.6.1-12_all.deb
dpkg -i povray-doc_3.6.1-12_all.deb
```

run from the same directory into which the files were downloaded.  Obviously substitute in the appropriate files for your own target architecture.  AFAIR POV-Ray doesn't have many dependencies; just a few basic graphics libraries.  It seems unlikely that directly installing it would break PNG.

---

### Post by CrimsonDynamo on 2012-06-11
just installed 12.04 and was able to get povray running.

followed the instructions here: [http://www.povray.org/download/linux.php](http://www.povray.org/download/linux.php)

and used the -no-arch-check option when installing:

sudo ./install -no-arch-check

you can do the same thing to run the test:

sudo ./install -no-arch-check test

Hope this helps.

---

### Post by sectio aurea on 2012-09-25
> **CrimsonDynamo said:**
> just installed 12.04 and was able to get povray running.

followed the instructions here: [http://www.povray.org/download/linux.php](http://www.povray.org/download/linux.php)

and used the -no-arch-check option when installing:

sudo ./install -no-arch-check

you can do the same thing to run the test:

sudo ./install -no-arch-check test

Hope this helps.

This also works for me in Ubuntu 12.10 Quantal Quetzal Beta 1, thanks. 

I'm getting some strange transparency artifacts in the test render window, though; not sure why yet.

---

