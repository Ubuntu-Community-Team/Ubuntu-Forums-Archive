---
title: "No boot unless hdd is selected from boot menu"
date: 2010-08-07
forum: General Help
---

### Post by MAHMAD550 on 2010-08-07
[B]Hi,

I have 2 HDD one of 1 TB and other of 250 GB on my Desktop, on my 250 HDD I installed Windows 7 and have tried creating a Dual boot but my System boots to Windows without giving me Booting options to Windows or Ubuntu, if I manually select the booting option by hitting the F8 Key shows me list of H/w to boot from, I select the 250 GB HDD and system now boots to Ubuntu, both OS works fine no issues but the glitch is why do I have to do this everytime when booting to Ubuntu.

I also tried clean installing Ubuntu after having removed the Windows 7 but the same problem, cannot boot unless the HDD is selected.

At the time of installation I also noticed that Ubuntu will not detect the Windows OS which was already there before installing Ubuntu, whereas I tried with the same disc on different laptop computer and it worked just fine, it detected windows 7 loader and gives the booting option.

I just want to know is it because of 2 HDD installed on my Desktop.

Any help would be appreciated.

Regards,
Haneef
[/B]

---

### Post by oldfred on 2010-08-07
Welcome to the forum.

Have you in BIOS changed the boot order. You probably still have the default which goes to the windows drive, while you have grub installed in the other drive. Some systems still call it primary master which it must be in older PATA/IDE systems.

Often if the grub osprober does not find the windows install during the installing of grub this will find it after you have booted into Ubuntu.

sudo update-grub

---

### Post by MAHMAD550 on 2010-08-08
[I][B]I did check the booting option in BIOS, its my default HDD, the thing that I am confused about is why windows is booting and why not Ubuntu if both are on the same HDD.

I guess I may have to try again installing.

Thanks for the prompt reply though.

Regards,
Haneef
[/B][/I]

---

### Post by oldfred on 2010-08-08
So we can see exactly what is where on your system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

