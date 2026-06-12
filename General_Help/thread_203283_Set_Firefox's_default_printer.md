---
title: "Set Firefox's default printer?"
date: 2006-06-25
forum: General Help
---

### Post by msak007 on 2006-06-25
I have a weird request / question, which on second thought doesn't seem that weird but I couldn't find anything anywhere on it. My question is whether or not it is possible to tell specific applications which printer to print to by default, specifically Firefox. The problem I'm having is Kubuntu / KDE specific, so here's the back story:

I'm sure all Kubuntu users would agree that Firefox by nature is a PITA to integrate into KDE because it's more Gnome-centric. In Kubuntu by default it only has 1 printer to choose from when printing: PostScript/default. I saw numerous posts all over the net and in the forums with a workaround to find the line 

```
print.postscript.print_command
```

in about:config and change its value to "kprinter" so that choosing PostScript/default brought up the kprinter dialog, where you could choose all the default printers installed (such as fax, PDF, etc). There's also a line you can add (not there by default) so that it'll print directly to the default printer without a dialog - so that it'll go straight to the kprinter dialog without having to choose PostScript/default every time and hitting Print, only to be taken to another dialog where you choose the printer to print to. So I added 

```
print.always_print_silent
```

to about:config, and set its value to "true". For a while every time I printed it  worked as advertised and went straight to the kprinter dialog. That all worked fine until I added a local printer...

After fiddling with a Lexmark Z53 and finally getting it working, Firefox now defaults to that printer. If I have the above print silent flag set to true, all prints go straight to the printer without a dialog. This was great when PostScript/default was the only printer, but now it prints to the Lexmark without prompting which is not what I want. 

So therein lies the problem - I want all prints from Firefox to default to the PostScript/default printer in the list so that it can go to the kprinter dialog first - there I can choose from any printer (including the Lexmark Z53). I've searched every printer-related setting in about:config / prefs.js, and cannot determine where Firefox is picking up the printer from. If I remove all Lexmark Z53-related entries from prefs.js, the next time I hit File --> Print, all those entries are re-added. Changing the default printer for the system really isn't an option, because then all apps will default to "PostScript/default", and that's not what I want. All I want is to tell Firefox ONLY to default to PostScript/default, so that it'll bring up the kprinter dialog automatically so that I can, for example, print to PDF, but still be able to choose the Z53 if I wanted to print to it. Either that or find some other way to have Firefox use kprinter instead of looking for CUPS printers only...

If anybody has any suggestions or workarounds, please let me know. I wish Firefox would integrate into KDE a little better...

EDIT: Just for clarification, I added 2 screenshots - one of the Firefox printer dialog, and one of the kprinter dialog when I choose "PostScript/default" and it opens up kprinter. You can obviously see that with kprinter I have all the options Firefox had and more, which is why I want it to default to that.

---

### Post by msak007 on 2006-06-25
I figured it out! There's really no way to set FireFox's default printer that I could find, but there *is* a way to tell it not to look at CUPS printers. I posted the full solution [here]("http://www.ubuntuforums.org/showpost.php?p=1180317&postcount=27") in case anybody wants to give it a shot. Basically you add the Boolean line 

```
print.postscript.cups.enabled
```

and set its value to "[COLOR="Red"]false[/COLOR]". In conjunction with the other lines I added, it defaults to PostScript/default and opens up kprinter.

---

