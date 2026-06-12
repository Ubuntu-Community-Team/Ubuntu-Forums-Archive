---
title: "Grub 2 Entries"
date: 2009-12-05
forum: General Help
---

### Post by Herr Skymarshall on 2009-12-05
Is there a way to remove kernel entries for Grub 2 without removing the kernel(s) and updating grub? The closest suggestion I can find is this:

 "To prevent a file in */etc/grub.d* from adding items to the menu, remove the *executable* bit or remove the applicable file." from [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

But after some exploring it is not obvious what I could remove the executable bit from and keep the system from breaking.

---

### Post by BigCityCat on 2009-12-05
I'm not sure if this is what you want.

[http://kubuntuforums.net/forums/index.php?topic=3108632.0](http://kubuntuforums.net/forums/index.php?topic=3108632.0)

---

### Post by ranch hand on 2009-12-05
I do not know what you have on your box so it is hard to give advice.

If you use a custom menu, built in your /etc/grub.d/40_custom file, and use the symbolic type menuentry, and you are not adding more OS', you can definately do away with the executable part of the permissions for the /etc/grub.d/10_linux and 20_memtest86 and 30_os-prober and 40_custom (if you built your custom menu and renamed the saved file to 06_custom).

This is the entry for one of my three 10.04 testing installations;
```

echo "Adding Daily on sda13" >&2 
cat << EOF
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
EOF

```
Note that this does not define the kernal.  It defines the partition.  It boots the newest boatable kernel that it finds at that partition.

I could install 9.10 on the same partition and not change that entry at all and it would work.

---

### Post by Herr Skymarshall on 2009-12-06
I'm dual booting 9.10 with Win 7. I didn't make any custom entries - Grub 2 auto found everything, I haven't tinkered with it much, so I'm basically using default Grub 2 settings.

---

### Post by ranch hand on 2009-12-06
I am glad to hear that grub2 found everything.

If you keep the old kernels they will be on your generated menu screen.  that is just the nature of the beast.

If you read the link in my sig you will have a better idea of how grub2 works.  There are great links included, particularly the first 3.  The 2nd and 3rd are from drs305 and he has sone extensive experimentation on grub2 since 9.10testing Alpha2.

9.10A2 is when we got grub2 and it was VERY rough.  We all had to play with it a lot.

If you add an entry like I said before, and add, in the same manner, your Win JerryLewis Pro entry, then save the file as 06_custom, those 2 entries will be at the top of your menu.

I do it this way on this box (except there is no MS).  This way I have the other entries to fall back on if I need to.

Right now I am on my test platform running 10.04testing.  I have 3 installs - Clean install from first Daily build - 9.10>10.04 upgrade - 9.04>9.10>10.04 upgrade.  All updated daily.

The 9.10>10.04 boots great.  The other 2 have some intractable problem with udevadm and will, currently only boot through recovery>return to normal boot>CLI log in>startx.

They run fine after that.  I try them every day to see if the new updates (testing gets LOTS of updates) has fixed the problem.  Not yet.

In your case, on a stable release, this is probably not needed.  Once you know that the custom file works you could remove the executable permission of the 10_linux through 40_custom files and that stuff would no longer be on your generated screen menu at all.

If you ran into problem you would have to chroot in from your live cd and return those permissions and run update-grub.

You can boot to recovery with the entry I gave you by hitting "e" and editing the "linux" line to read;
```

[FONT=monospace]linux /vmlinuz root=/dev/sda13 single

```
There really is a lot more you can do with grub2 than with grub-legacy.  It just takes complete retraining.
[/FONT]

---

### Post by Herr Skymarshall on 2009-12-06
Thanks for the info and the link! :)

---

