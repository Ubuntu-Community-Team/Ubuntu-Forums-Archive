---
title: "Wine problems"
date: 2011-08-07
forum: General Help
---

### Post by ThatIdiot on 2011-08-07
I having some trouble with Wine. I tried running the 'make uninstall' command, but:

```
make[1]: Entering directory `/home/brandon/wine-1.3.19/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/brandon/wine-1.3.19/tools'
make[1]: Entering directory `/home/brandon/wine-1.3.19/dlls/acledit'
cd /usr/local/lib/wine && rm -f acledit.dll.so  
rm: cannot remove `acledit.dll.so': Permission denied
make[1]: [uninstall] Error 1 (ignored)
rm -f /usr/local/lib/wine/fakedlls/acledit.dll
rm: cannot remove `/usr/local/lib/wine/fakedlls/acledit.dll': Permission denied
make[1]: *** [uninstall] Error 1
make[1]: Leaving directory `/home/brandon/wine-1.3.19/dlls/acledit'
make: *** [uninstall] Error 2

```

I can't remove through terminal, and I can't remove it manually. I tried just removing everything through winetricks, then removing everything through synaptic, but whenever I install from software center, I'm back to wine 1.3.19. :mad:

---

### Post by CatKiller on 2011-08-07
Why are you compiling an old version from source? 1.3.25 is in the [Wine PPA]("http://www.winehq.org/download/ubuntu") at the moment, and .26 should be there soon. Much simpler.

---

### Post by ThatIdiot on 2011-08-07
I was using .19 for a bit, updated to .25 then .26, went back to .24 (because I'm having problems with audio in .25 and .26). Every time I started up a game it would say it was updating wine's config, as if I had just installed Wine. I thought if I got rid of everything and installed through PPA, that problem would be gone.

In .25 and .26, I'm getting no audio at all. 
I just tried updating to .25, but it's still on .19. Cleared wine through winetricks, deleted everything wine-related, tried to update again, went back to .19. :|

---

### Post by CatKiller on 2011-08-07
> **ThatIdiot said:**
> ```
rm: cannot remove `acledit.dll.so': Permission denied
```

You need to run make uninstall as root, the same as make install. You're changing files outside your Home directory, which a normal user can't do.

For future compiling, checkinstall is a good program. It generates a .deb that gets installed in the usual way. Makes removing and updating compiled programs easier.

---

### Post by ThatIdiot on 2011-08-07
oh yeah, that was another problem I was having. when I ran as root I got:

```
rmdir /usr/local/share/wine /usr/local/lib/wine/fakedlls /usr/local/lib/wine
rmdir: failed to remove `/usr/local/lib/wine/fakedlls': Directory not empty
rmdir: failed to remove `/usr/local/lib/wine': Directory not empty
make: [uninstall] Error 1 (ignored)

```

not sure what I could do about that. I tried getting rid of it myself, but I don't have permissions to all of those folders and files.

---

### Post by .... on 2011-08-07
```
sudo rm -rf /usr/local/wine
rm -rf ~/.wine
```

---

### Post by ThatIdiot on 2011-08-07
thanks, guys. I was able to install the latest wine without having everything update whenever it opened. I have another problem though, and I didn't wanna make a new thread for it:

I went to the wine forums and it said to run 'killall pulseaudio' It fixed my wine audio problems, but now I can't control my volume and whenever I try to go into the sound preferences I get "Waiting for sound system to respond"

---

### Post by .... on 2011-08-07
Use pasuspend to run wine if you must stop pulseaudio. Use another mixer (alsamixer or xfce4-mixer) to control volume without pulseaudio.

---

