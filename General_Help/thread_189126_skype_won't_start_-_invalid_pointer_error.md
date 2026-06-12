---
title: "skype won't start - invalid pointer error"
date: 2006-06-04
forum: General Help
---

### Post by BioTeX on 2006-06-04
After upgrading to dapper and installing the latest version of skype, I can't get it to even start.  I get this error:

```
*** glibc detected *** free(): invalid pointer: 0x08a242c8 ***
Aborted

```

After also installing the skype-dsp-hijacker ( see []("http://www.ubuntuforums.org/showthread.php?t=171761") ), I have the same problem, and it says:

```
hijacker: skype_dsp_hijacker v0.6
hijacker: when Skype opens DSP /dev/dsp
hijacker: - microphone used: /dev/dsp
hijacker: - speakers used:   /dev/dsp
hijacker: when Skype opens mixer /dev/mixer
hijacker: - mixer used: /dev/mixer
*** glibc detected *** free(): invalid pointer: 0x08a242c8 ***
Aborted

```

I'm running on a HP pavilion zd7000 laptop with a pentium 4.  Any thoughts?

---

### Post by Evoreth on 2006-06-05
The same happens for me as well. I'm using Ekiga now. :roll:

---

### Post by BioTeX on 2006-06-05
Yeah, Ekiga's nice.  But with Skype I was enjoying the free SkypeOut service to call land lines (which remains free for the rest of 2006).

---

### Post by ushaba on 2006-06-05
i'm having the same problem. unfortunately most of my acquaintances only use skype. i followed the forum post on this earlier,
[http://www.ubuntuforums.org/showthread.php?t=171761](http://www.ubuntuforums.org/showthread.php?t=171761)

as well as all of the pages it links to, and still have the same problem. currently using xubuntu 6.06. is anyone having any success on this?

---

### Post by ushaba on 2006-06-05
i just discovered something really strange. i did a fresh reinstall out of absolute frustration, and forgot that dapper sets my language preference as "english hong  kong." i was messing around with scim to get it working in en_US, but haven't dared try it with en_HK yet for the *following reason*: after fixing scim, skype is broken. the same error with the pointer. so right now i have a choice between skype or chinese input, which is a shame if i'm talking to someone who only speaks chinese... en_US uses scim, en_HK can use skype. HK is default for the locale, but i'm really nervous about adding a .xsession file telling scim to be my default im environment or doing an im-switch... can someone who understands the file system a little better than i do suggest what scim, the locale, and the xsession have in common? 
thanks for any help you can give!

---

### Post by BioTeX on 2006-06-05
Ahh, interesting.  I have scim installed too, for typing in Japanese.  I already did an im-switch to make it the default input method.  I'm actually not sure how to switch it back.:-k

---

### Post by Evoreth on 2006-06-05
I'm using scim for Japanese input, too. This problem seems to be more complicated than I thought. Any ideas?

---

### Post by BioTeX on 2006-06-05
Well, you can uninstall scim and use uim instead.  But, as I recall, uim broke my ability to add a printer in breezy.  What is it that makes input methods have these weird conflicts?

---

### Post by ushaba on 2006-06-06
[QUOTE=BioTeX]Well, you can uninstall scim and use uim instead.  But, as I recall, uim broke my ability to add a printer in breezy.  What is it that makes input methods have these weird conflicts?[/QUOTE]


i don't know man... that may work fine for japanese, but uim is somewhat of a nightmare for chinese. i suppose i could screw around with the input method switcher in one of my other "english" environments, as i'm pretty sure i'll never be operating in "en_IN" mode. 

as it stands, every time i install i spend at least a day or two configuring xorg.conf, pppoeconf (first have to set it up as dhcp, steal the ifconfig info, then reset network-admin with a static ip, re-do pppoeconf...) scim, skype, sound, etc. it's supposed to "just work" but that has been anything but the case for me. i've got it down to something of a science now with regards to xorg.conf and the network thing, having done it in mandrake too, but this input method thing, especially in breezy, almost made me switch away from ubuntu. then again, i haven't even TRIED setting up wifi on dapper... haha

---

### Post by ushaba on 2006-06-06
i found a *bad* way around this problem. i currently have both skype and scim working, but the two cannot coexist...ie, i can't type in chinese in skype. at least this way i don't have to restart x constantly. according to an archlinux forum and a few taiwanese sites (i'll use the english link for archlinux since you're japanese speakers), acroread, realplayer, skype and scim cannot get along peacefully. to get skype, acroread, or realplayer (i haven't tried this with realplayer since i don't use it on principle), type:
           
      XMODIFIERS=@im=none QT_IM_MODULE=xim skype 

(or acroread, or realplayer)

i wish i could find a way to automate this, but the scim /usr/bin/scim script is not a shell script like the one for acroread. you can see the fix for acroread permanently in the link. so right now i have chinese and skype coexisting... sort of. let me know if this works for you guys.

[http://bbs.archlinux.org/viewtopic.php?t=11551&highlight=scim+acroread](http://bbs.archlinux.org/viewtopic.php?t=11551&highlight=scim+acroread)

to view what scim has to say about this...
[http://www.scim-im.org/wiki/faq/general/is_it_possible_to_prevent_ctrl_space_from_activating_scim_in_some_apps](http://www.scim-im.org/wiki/faq/general/is_it_possible_to_prevent_ctrl_space_from_activating_scim_in_some_apps)

---

### Post by BioTeX on 2006-06-06
Hmm, not bad.  I guess you could use the menu editor to change the command for the Skype launcher in the applications menu.

---

### Post by dmizer on 2006-07-05
[QUOTE=BioTeX]Well, you can uninstall scim and use uim instead.  But, as I recall, uim broke my ability to add a printer in breezy.  What is it that makes input methods have these weird conflicts?[/QUOTE]
anthy is what broke your ability to add a printer.  and it didn't really break your ability to add a printer (you could still have used the web interface for cups), it just broke gnome's print add gui (which also still worked by logging in as japanese).

i don't know that there's any easy way to get japanese input without anthy, but both scim and uim are capable of using anthy.

edit to add:
this is ubuntu specific.  i am currently running scim with skype in fedora core 5 with no issues.  additionally, with this set up i have no problem typing japanese in skype.

---

### Post by gomez_in_the_south on 2007-06-06
> **ushaba said:**
> 
type:
           
      XMODIFIERS=@im=none QT_IM_MODULE=xim skype 



After installing SCIM I had the same problem. this solution worked for me - thanks ushaba.

---

