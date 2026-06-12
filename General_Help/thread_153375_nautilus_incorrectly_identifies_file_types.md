---
title: "nautilus incorrectly identifies file types"
date: 2006-03-31
forum: General Help
---

### Post by droazen on 2006-03-31
Hi,

I have a couple directories filled with *.smc files - these are all ROM images. I would like to associate a program with these files so that I can open them from within nautilus, but unfortunately nautilus seems to think that some of them are of type "Truetype Font", others are of type "Text Document", and others are of type "SMC Document". I can associate a program with the ones identified as being "SMC Documents" just fine - but I can't associate with the ones identified as text files or fonts without causing ALL text files/fonts to open in that program.

Since these files all have the same .smc extension, I suspect that nautilus is looking at the contents of the files to try to determine their type. How can I tell nautilus to ONLY look at the extensions when determining file type?

Any help is appreciated :)

---

### Post by BoyOfDestiny on 2006-04-02
[QUOTE=droazen]Hi,

I have a couple directories filled with *.smc files - these are all ROM images. I would like to associate a program with these files so that I can open them from within nautilus, but unfortunately nautilus seems to think that some of them are of type "Truetype Font", others are of type "Text Document", and others are of type "SMC Document". I can associate a program with the ones identified as being "SMC Documents" just fine - but I can't associate with the ones identified as text files or fonts without causing ALL text files/fonts to open in that program.

Since these files all have the same .smc extension, I suspect that nautilus is looking at the contents of the files to try to determine their type. How can I tell nautilus to ONLY look at the extensions when determining file type?

Any help is appreciated :)[/QUOTE]

Yeah, indeed we have the same issue... I have all my snes roms in JMA format (basically just a compression format). I used nsrt [http://nsrt.edgeemu.com/forum/portal.php](http://nsrt.edgeemu.com/forum/portal.php), luckily it worked under amd64 with the ia32libs... Zsnes and snes9x can handle the format.

I guess I would like to do the same with my nes, gb, etc... I'd like 1 rom per compressed file, it's not as a space efficient, but I don't think emulators could load it from one big tar... 

To any scripting masters, go through a directory, each file gets it's own tar...

i.e. 1.nes 2.nes 3.nes
run the script
you get 
 1.nes 2.nes 3.nes
 1.tar.gz 2.tar.gz 3.tar.gz

One would still have to right click the file to launch it, but I'd prefer that over it being incorrectly identified...

EDIT: I'll be googling for a script like that, it would be quite handy... And maybe even write one, if this is something trivial... ;)

---

