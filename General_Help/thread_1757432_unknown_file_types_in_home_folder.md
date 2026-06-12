---
title: "unknown file types in /home folder"
date: 2011-05-13
forum: General Help
---

### Post by filligree on 2011-05-13
I've recently upgraded from 10.04 to 10.10 (a bit late, I know), but have been getting repeated messages telling me that the filesystem is running low on space.

I've run apt-get autoremove and autoclean, but there is still insufficient space for me to upgrade to 11.04.

Whilst looking through the /home folders, I came across a number of 2 character titles folders in the /home/user directory.  These have the extension.file.  Does anyone know what they are, and can I delete them?

:confused:

---

### Post by TeoBigusGeekus on 2011-05-13
What's their content and their full names?

---

### Post by filligree on 2011-05-13
The first folder is /home/emma/97, and contains the following files:

19cba5a1081f1363c854552ef9a3ae5dd3f42f32.file
19ce9b17a3b6b97b4154b14df7b6ffd304646522.file
19e58a797ac90314c0923f8986c14f044a6ac950.file

and another 7 similarly named files.  I can't open them with a text editor to view the contents, I get the following error:

"Could not open the file /home/emma/19/19ce9b17a3…b14df7b6ffd304646522.file.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

opening in open office word processor gives me the following characters:

"@OB'6›êˆ‹:Z,—êú#Á´!Céq‰&#65533;àŒŠ½ô(#L/U#öç\L7òxøOá¼†é(FuÌI#úäR½ü	§µÆµ#(me>#Ñ·{SNL=ÃtÀg%ürÈFráÍ‹#ì¶[Jç##Ö´+½ô¿æt*i“
#u&#65533;ÔîØ„###&#65533;ß#i¸©°(ê¶21›~Hrš2|ÍÍA&#65533;IâXÍ½Ô¦Ù›5!ö\)#w:&S›z[PJ#&#65533;#5{8ˆ§¶9´ô*Üšœi#¶xÿÔx§6tdm´ûXJ2»÷#bI—Žk¡¬º¸ÇZÂž3@*¨éa¥qç§*&#65533;OÌûPüi·Ñ+ž˜Úv÷rÜ»*è<70ç6g#&#65533;#(hBôÂ#‰T_ed8
t*õ&fðj‘æ&#65533;k#ÉŸ`¦×·cçB4ŠfüVMz#Öw\Œ„	#î#û”æ–á;dÓD¢‚?ö¾#Õ#.8øœÄÔ*Ù]ø#Ý¾^ôöÎ´´0\@B#•{v½ln#R¨¢`˜ëŠHZêJã¬¯¯E@–Ø"

the same folder is attached, in case that helps.  the others all appear to be of a similar nature.

---

### Post by TeoBigusGeekus on 2011-05-13
Are they large in size?

---

### Post by lithopsian on 2011-05-13
Delete them (to trash) and see what breaks :)

---

### Post by filligree on 2011-05-13
OK, after a bit of trial and error, a couple of sample files attached.

---

### Post by filligree on 2011-05-13
Some are large (>1.5MB), the rest are less than a MB.  the amount I have though makes for quite a volume of files.

---

### Post by TeoBigusGeekus on 2011-05-13
Tar'em all, delete the originals, reboot and see if everything works ok.
If so, delete the tarballs as well.

EDIT:
On second thought, these must be the temporary files from the failed attempt to upgrade to 11.04. Deleting them won't change much - upgrade wise.
After you've deleted them, originals and tarballs, post us the output of
```
df -h
```

---

### Post by filligree on 2011-05-13
df -h gives:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              16G   13G  2.3G  86% /
none                  243M  256K  243M   1% /dev
none                  249M  188K  249M   1% /dev/shm
none                  249M  392K  248M   1% /var/run
none                  249M     0  249M   0% /var/lock
/dev/sdb1              17G   11G  6.1G  65% /media/Win
/dev/sda1             154G   20G  127G  14% /media/seagate1_
/dev/sda2              97G   24G   69G  26% /media/seagate2_
/dev/sda3              44G  4.1G   38G  10% /media/seagate3_


---

### Post by TeoBigusGeekus on 2011-05-13
You need to move some things from your home partition to your other partitions: songs, videos, large pdfs, anything that takes space.

---

### Post by AlphaLexman on 2011-05-13
The 'file' command will read the header information of ANY file and tell you the filetype.
```
file 19cba5a1081f1363c854552ef9a3ae5dd3f42f32.file
file 19ce9b17a3b6b97b4154b14df7b6ffd304646522.file
file 19e58a797ac90314c0923f8986c14f044a6ac950.file
```

---

### Post by TeoBigusGeekus on 2011-05-13
> **AlphaLexman said:**
> The 'file' command will read the header information of ANY file and tell you the filetype.
```
file 19cba5a1081f1363c854552ef9a3ae5dd3f42f32.file
file 19ce9b17a3b6b97b4154b14df7b6ffd304646522.file
file 19e58a797ac90314c0923f8986c14f044a6ac950.file
```

I've done that with the op's attachments; it just says "data".

---

### Post by filligree on 2011-05-13
the biggest folder on that partition is /usr @ 6.6GB, then /home  2.2GB.  I've removed most of the files I can from the /home folder already.

Any other suggestions?

---

### Post by TeoBigusGeekus on 2011-05-13
Have you installed a lot of apps on your pc?

---

### Post by filligree on 2011-05-13
Not a huge amount, no.  I;ll go through and uninstall the ones I don't use, or I've superseded with something else, and see how I'm doing I guess.

---

### Post by TeoBigusGeekus on 2011-05-13
I'd also suggest installing bleachbit (ccleaner equivalent for linux) and running it both as a user and as root - it might save you some space.
Good luck.

---

### Post by AlphaLexman on 2011-05-13
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              16G   13G  2.3G  86% /
none                  243M  256K  243M   1% /dev
none                  249M  188K  249M   1% /dev/shm
none                  249M  392K  248M   1% /var/run
none                  249M     0  249M   0% /var/lock
/dev/sdb1              17G   11G  6.1G  65% /media/Win
/dev/sda1             154G   20G  127G  14% /media/seagate1_
/dev/sda2              97G   24G   69G  26% /media/seagate2_
/dev/sda3              44G  4.1G   38G  10% /media/seagate3_ 			 		

Which drive is '/' mounted on and which drive is '/home' mounted on?
It looks like you have MS Windowz on '/dev/sdb1', and...
It looks like '/dev/sdc1' is very full, but...
It looks like '/dev/sda1', '/dev/sda2', and '/dev/sda3' **ALL** have plenty of free space... 

Maybe you could move '/home' to another drive 'sda?'

---

### Post by TeoBigusGeekus on 2011-05-13
Apparently she doesn't have a separate home partition...

---

