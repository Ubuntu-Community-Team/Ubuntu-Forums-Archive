---
title: "Last Resort, Can you help me with Wine?"
date: 2006-04-12
forum: General Help
---

### Post by bixin on 2006-04-12
Okay, I have been at this for 2 days. I searched and searched the forums tried most of it but nothing is working. I tried gazj's how to and Automatix and the segmentation fault remains. I don't know what more to do. Automatix gives me this: [PHP] Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/barbara', starting in the Windows directory.
Segmentation fault
[/PHP]

Using gazj's how to and winetools gives me:  [PHP]Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
/usr/bin/wineprefixcreate: line 173: 15303 Segmentation fault "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
/usr/local/bin/wt: line 130: 15313 Segmentation fault winecfg -D
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Drive C: is /home/barbara/.wine/drive_c, links will be made for c fake_windows
Linking /home/barbara/.wine/drive_c to c...
Linking /home/barbara/.wine/drive_c to fake_windows...
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files"
mv: cannot move `/home/barbara/.wine/c//Program Files' to a subdirectory of itself, `/home/barbara/.wine/c/Program Files/Program Files'
rmdir: `/home/barbara/.wine/c/': Not a directory
ln: `/home/barbara/.wine/c//Program Files': cannot overwrite directory
Linking "/home/barbara/.wine/c/" to "/home/barbara/.wine/c/Program Files/Common Files"
rmdir: `/home/barbara/.wine/c/': Not a directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot open (null)
no suitable Wine directory found...
Wine 0.9.5
wine is executed as wine
Parameters are NEW
Wine is not configured yet![/PHP] This brings me back to the beginning of the winetools base menu. I have followed directions as stated, it was suggested that I didn't have permission but I am mostly sure that I do. I will look around and see what I can find on the permission thing. It could be back to Windows for me, please don't let that happen. I hate asking but even just a point in a right direction is good enough, help me! 

Thanks :KS

---

### Post by philipacamaniac on 2006-04-12
Oh heavens! Don't go back to Windoze! (j/k)

Try this. Using Synaptic, completely remove wine and winetools. Then in Nautilus, from the Edit menu (I think), choose "Show Hidden Files" and browse to your Home directory (/home/barbara). Find the ".wine" directory and delete it.

Now, back in Synaptic, reinstall wine and winetools. Once they are installed, from a terminal, type "wt" to run winetools, and make sure you don't run it as root! (Don't do "sudo wt"). That should give you a proper wine configuration. What program do you need to run in Wine?

---

### Post by bixin on 2006-04-12
Okay, I have a question how do I remove winetools it is not found in Synaptic and doesn't seem to want to be deleted

---

