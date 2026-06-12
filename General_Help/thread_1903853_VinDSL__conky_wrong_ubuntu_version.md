---
title: "VinDSL  conky wrong ubuntu version"
date: 2012-01-03
forum: General Help
---

### Post by elliotn on 2012-01-03
I setup conky as the one on VINDSL tutorial but it shows I run ubuntu 12.0 alpha 1 while I run ubuntu 11.10, why

---

### Post by VCoolio on 2012-01-03
The vindsl setup seems to run lsb_release -sd, so what does that tell you in a terminal? You didn't by any change update all your system to latest alpha? Post your conky config (especially the part below TEXT) so we can have a look.

---

### Post by elliotn on 2012-01-04
> **VCoolio said:**
> The vindsl setup seems to run lsb_release -sd, so what does that tell you in a terminal? You didn't by any change update all your system to latest alpha? Post your conky config (especially the part below TEXT) so we can have a look.

```
# ${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=8.1}${color4}alpha 1${font}

```

```
elliotn@elliotn-G31-M7-TE:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
elliotn@elliotn-G31-M7-TE:~$ 

```

---

### Post by elliotn on 2012-01-04
any ideas

---

### Post by VCoolio on 2012-01-04
this makes no sense. The first line executes "cat /etc/*release{print $2}'" which is wrong. Also it's commented so maybe it's not meant to be there. The last line just prints "alpha 1", it's not the result of any command. It's just text. 

So try like this:```
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec echo `lsb_release -rs` `lsb_release -cs`}${font}
```

You may need to play with the voffset stuff to get the output in the right spot. Also maybe you want something else than what lsb_release -rs and -cs gives you. Run "man lsb_release" in a terminal to check the options.

---

### Post by 42dorian on 2012-01-04
In the latest script by VinDSL, he does have his particular version hard coded.  It's probably better if you just change the hard code yourself to your version.

I will make an update to the Howto to catch this if possible.  Thank you for bringing it to my attention.

---

