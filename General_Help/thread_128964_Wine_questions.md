---
title: "Wine questions"
date: 2006-02-12
forum: General Help
---

### Post by el3ktro on 2006-02-12
Hello,
I'm setting up a new comp for my family, and they still need some Win programs (Micrografx Designer (ugh!) & "WISO Büro komplett". I try to get both working in Wine. I've apt-getted the newest Wine (0.9.7). I ran winecfg, just tweaked the drives setup a little & didn't touch the rest. Micrografx Designer installed flawlessly, and actually also runs flawlessly. The only problem that it uses a real weird font for the UI, and I don't know how to change that. All infos I've found always refer to a file called ~/.wine/config - but this file doesn't exist on my system. How can I change the UI default font?

The other program is a little more tricky. The installer again works flawlessly, but when I then start the program the splash appears, but then it says "Interface not supported".

Well my question is as follows: Afaik Wine has it's own DLLs, but optionally you can also use the original Windows DLLs. Couldn't I just copy over all the necessary DLL's from the Windows-XP-dual-boot install to the Wine dir? Would this work? Would it be a good idea to do so? I could set up a fresh WinXP (or Win2k), do nothin with it except installing Micrografx+this other software and then copy over all the DLLs or probably even the complete Win system, incl. registry etc.

I don't know much about Wine, so any clarification of this would be appreciated!


Tom

---

### Post by bluevoodoo1 on 2006-02-12
[QUOTE=el3ktro]The only problem that it uses a real weird font for the UI, and I don't know how to change that. All infos I've found always refer to a file called ~/.wine/config - but this file doesn't exist on my system. How can I change the UI default font?

winecfg &Couldn't I just copy over all the necessary DLL's from the Windows-XP-dual-boot install to the Wine dir? Would this work? Would it be a good idea to do so? [/QUOTE]

1. You could open .wine/drive_c/psfonts and see what fonts are there. I had a font problem before when I installed Finale with wine and the terminal only displayed funny symbols and music notation. I copied a couple of fonts from my /usr/share/fonts/truetype/freefont folder to .wine/drive_c/psfonts and the font problem was fixed. I don't know how, yet, to make wine use a 'default' font... Don't know if that will help at all...

2. I copied over a DLL from my XP system to make Finale work and everything seems to be working fine.

---

### Post by el3ktro on 2006-02-12
[QUOTE=bluevoodoo1]1. You could open .wine/drive_c/psfonts and see what fonts are there. I had a font problem before when I installed Finale with wine and the terminal only displayed funny symbols and music notation. I copied a couple of fonts from my /usr/share/fonts/truetype/freefont folder to .wine/drive_c/psfonts and the font problem was fixed. I don't know how, yet, to make wine use a 'default' font... Don't know if that will help at all...

2. I copied over a DLL from my XP system to make Finale work and everything seems to be working fine.[/QUOTE]

1. When you copied over this XP DLL, what Windows version did you define in Wine's config file?

2. How do I know which DLLs a program needs? The WISO software spits out a few lines of error messages, but I haven't found any evidence of a DLL in there so I have no idea which one to copy ...


Tom

---

### Post by bluevoodoo1 on 2006-02-12
I said I was using XP since that's where it came from. I can't remember exactly. I don't think I ever had to change anything in winecfg.

I only needed 1 DLL since upon opening the program (via terminal), it gave an error telling me the DLL that was needed.

---

### Post by dcstar on 2006-02-13
[QUOTE=el3ktro]Hello,
......
Well my question is as follows: Afaik Wine has it's own DLLs, but optionally you can also use the original Windows DLLs. Couldn't I just copy over all the necessary DLL's from the Windows-XP-dual-boot install to the Wine dir? Would this work? Would it be a good idea to do so? I could set up a fresh WinXP (or Win2k), do nothin with it except installing Micrografx+this other software and then copy over all the DLLs or probably even the complete Win system, incl. registry etc.

I don't know much about Wine, so any clarification of this would be appreciated!

Tom[/QUOTE]
AFAIK some wine dlls provide the links into Linux, so replacing them may totally break wine.

---

