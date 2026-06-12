---
title: "Why didn't my files get found"
date: 2010-03-12
forum: General Help
---

### Post by tropdoug on 2010-03-12
I was seaching for a particular file (WAV) and using 
Applications>Places>Search for files resulted in finding none of the files I was supposed to have (see [http://ubuntuforums.org/showthread.php?t=1428461](http://ubuntuforums.org/showthread.php?t=1428461)) 

However I then used Gnome Do and bingo there was one of them, then used the "reveal" option and there were all my files. 

Does anyone know why the ubuntu file search facility could not find them , but the Gnome Do could? 

By the way in the system search facility I sued *.wav and found other wav files, and then used DA* (DA being the first two letters of the file) and found all sorts of data labeled files etc, but none of the ones I was looking for. In 'Gnome Do' I typed 'DA' and there it was. I would really like to know the answer for future reference.

Douglas

---

### Post by ram2500 on 2010-03-12
I think the Gnome utility is similar to Windows' way of indexing, where the indexing program works in the background. Therefore, not every file would be available through the search tool until it has been indexed--thus, your WAV file may have not been indexed yet. If the search tool in Ubuntu is similar to Windows indexing, then this would be the case.

---

### Post by Herman on 2010-03-13
:D Ah the Rex Lookoff just north of Hartley's Creek on the road to Port Douglas. 
Nice avatar!

---

### Post by tropdoug on 2010-03-13
Your either a local or got a similar photo, yes your right, and it's one of the mamy beaufspots  magnificent part of the country. I am very grateful to have the privilege of living & working in Cairns 

(and then he glances up to see your a Hughenden lad) how you faring with the wet?

---

### Post by tropdoug on 2010-03-13
Ok, that might explain it. I am always curious to try and build my understanding of how Linux works. 

Incidentally once I did find the files I want I am busily converting them to MP3 using a program called audioconvert (its a nautilus script) it is awesome, whoever wrote it deserves a medal. So far I have converted 600 WMA and wav files and not one fault. Lets see winblows match that!

---

### Post by victor.zamanian on 2010-03-13
tropdoug, `gnome-search-tool', which is what you used, doesn't use any indexing other than perhaps the 'locate' program. From the man page:

"GNOME  Search  Tool  uses the find, grep, and locate UNIX commands. [...]"

The `locate' tool does use a database. But not find or grep.

Could the problem be that you weren't looking in the correct folder, or that some other filter was active that was filtering out your results? I was using the gnome-search-tool at times before, but left it for the `find' commandline tool. :) Once you get used to find, it's pretty darn sweet.

$ man find

---

