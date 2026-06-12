---
title: "help with customizing grub 2 bootloader"
date: 2010-07-27
forum: General Help
---

### Post by staterunner180 on 2010-07-27
so i just got the grub 2 bootloader working, but for some reason it wont let me apply themes. i can open up all the files and edit them, and saved them the way i wanted them changed, and all these changes stay. but when i go into terminal to update grub this happens 

```

ryan@ryan-desktop:~$ sudo update-grub

[sudo] password for ryan: 

Generating grub.cfg ...

/etc/grub.d/05_debian_theme: line 48: unexpected EOF while looking for matching ``'

ryan@ryan-desktop:~$ 

```

---

### Post by LegendofTom on 2010-07-28
Looks like a syntax error in /etc/grub.d/05_debian_theme.  Check line 48 or around there and make sure you have the right number of backticks.

Legend

---

### Post by staterunner180 on 2010-07-28
well here is what it says, beginning at line 48 from the top:


```

if [COLOR=Magenta]background_image `[/COLOR]make_system_path_relative_to_its_root [COLOR=Magenta]${bg}` ;[/COLOR] then
  set [COLOR=Magenta]color_normal=white/black[/COLOR]
  set [COLOR=Magenta]color_highlight=aquamarine/black[/COLOR]
else
[COLOR=Magenta]E0F
[COLOR=Black]fi[/COLOR]
[/COLOR]
```

and the fi is the very bottom.
i changed 'color_normal=white/black' to change the text color in grub2, but i don't remember what it said before. it wasn't black/black though, i know that. and the same for 'color_highlight=aquamarine/black'
but i'm sure that i didn't touch the line starting with 'if background...' but that's line 48. so how can something be missing if i didn't take anything away?

---

### Post by staterunner180 on 2010-07-28
i tried deleting the line "E0F" which is the 2nd to last in the code box of my last post, and that got me the same result, so i just put it back in :( can someone please help me with this? maybe give me a copy of what their portion of that file looks like so i can replace it?

---

### Post by staterunner180 on 2010-07-28
Maybe i should try a clean installation of grub? like putting in the LiveCD and reinstall grub2. not ubuntu. just grub? someone please help! i'm sort of a newbie.

BUMP

---

### Post by LegendofTom on 2010-07-28
Here is what I have for that section:

```

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

```

---

### Post by staterunner180 on 2010-07-28
thanks for that but still the same problem. i think i might have a solution though. could you please put your line of text from where it says 
```

# check for usable backgrounds

```

to
```

     fi
    fi
   done
 fi

```

i do believe i am missing a back tick there, and i'm not exactly sure how to count the lines haha. do i include the spaces or what? anyways, its about halfway down.

also, i tried reinstalling grub 2 from the LiveCD but no matter which partition i told terminal to use, it said it was a BAD idea. literally.

---

### Post by LegendofTom on 2010-07-28
```

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

```

---

### Post by dino99 on 2010-07-28
either:

sudo aptitude install grub2-splashimages

or try burg

[http://www.s4nji-blog.com/2010/05/installing-burg-on-ubuntu-lucid-lynx.html](http://www.s4nji-blog.com/2010/05/installing-burg-on-ubuntu-lucid-lynx.html)

---

### Post by staterunner180 on 2010-07-28
okay so i got the problem with not updating grub fixed. i was just missing one back tick. stupid programming. haha, anyways i have a new problem:

whenever i type in 'sudo update-grub' i get this:
```

ryan@ryan-desktop:~$ sudo update-grub
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: 4: source: not found
/etc/grub.d/05_debian_theme: 42: /usr/share/images/desktop-base/moreblue-orbit-grub.tga: Permission denied
/etc/grub.d/05_debian_theme: 42: is_path_readable_by_grub: not found
/etc/grub.d/05_debian_theme: 42: is_path_readable_by_grub: not found
/etc/grub.d/05_debian_theme: 54: --target=device: not found
/etc/grub.d/05_debian_theme: 54: prepare_grub_to_access_device: not found
/etc/grub.d/05_debian_theme: 54: make_system_path_relative_to_its_root: not found
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found Microsoft Windows XP Home Edition on /dev/sdb1
done
ryan@ryan-desktop:~$ 

```

I can't for the life of me figure out why the moreblue-orbit-grub.tga is denied. its my own personal background for the boot screen, it just renamed it to what grub had there originally, and put it in that folder. i tried putting a different path to the same file but i got the same result. Is there something wrong with the picture? It's one from the splash images download.

And also, why can't all those other things be found?

I wish i could make myself be happy with just editing the text colors for the boot menu, but what can I say, it's the jailbreaker coming out in me ;)

---

### Post by LegendofTom on 2010-07-28
Try changing the permissions on oreblue-orbit-grub.tga.  And I suspect the rest of your errors are a byproduct of not taking your background.

---

### Post by staterunner180 on 2010-07-28
i took someone's (not sure who it was) advice and went ahead and installed burg. i no longer get those annoying not found erroers!! :D and i've figured out how to change the resolution and did that. now the only hitch left is applying the sora theme that came with burg. i've told 2 different files in burg to use the sora theme. 
```

/etc/default/burg

```

and also:
```

/etc/burg.d/00_header

```
but neither of them applied the theme, even though terminal says this:
```

ryan@ryan-desktop:~$ sudo update-burg
[sudo] password for ryan: 
Generating burg.cfg ...
Found theme: /boot/burg/themes/sora/theme
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found Microsoft Windows XP Home Edition on /dev/sdb1
done
ryan@ryan-desktop:~$ 

```

---

### Post by staterunner180 on 2010-07-29
Okay, this is going to be my last post on this thread if no one else decides to post on it. 

Here is what's happened so far:

I had trouble theming GRUB 2, even though its supposed to be easy. I had a bunch of problems with files not being found and whatnot. So I then installed BURG.

Now, with BURG, when I update it all the files are found. But I still want to theme it. So i edited both this file:
```

/etc/burg.d/40_custom

```
And this file:
```

/etc/burg.d/00_header

```to use
```

/boot/burg/theme/sora/theme

```as the theme. These files do not point to a theme.txt file, but a plain theme file. All guides on all the websites I have visited say to use theme.txt, but that's not what the file in my folder is.

And I know its not a case of the files not listening to me, because I made the resolution on the file
```

/etc/burg.d/00_header

```1024x786 rather then 640x480, and it worked. This isn't going to be left this way though. If I can get the themes to work then I realize the resolution must be 640x480. 

And also, when i type 'sudo update-burg' into terminal it says this:
```

ryan@ryan-desktop:~$ sudo update-burg
[sudo] password for ryan: 
Generating burg.cfg ...
Found theme: /boot/burg/themes/sora/theme
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found Microsoft Windows XP Home Edition on /dev/sdb1
done
ryan@ryan-desktop:~$ 

```So I know it sees the theme, it just needs to apply it!

So like I said above, if no one helps me I will most likely leave this thread open and deal with not having a theme for the boot menu. I may check back periodically, but not often. If you want my full attention, please reply soon.

BUMP

---

### Post by staterunner180 on 2010-07-29
Oh and I also told 
```

/etc/default/burg

```
to use the Sora theme as well.

---

