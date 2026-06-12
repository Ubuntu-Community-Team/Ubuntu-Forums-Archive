---
title: "&quot;invalid encoding&quot; for files on NAS"
date: 2011-01-23
forum: General Help
---

### Post by kelsoKashka on 2011-01-23
I've recently switched from Windows to Ubuntu Studio (11.04), and my only remaining problem is the encoding of the file names in my music collection. The music files are on a D-Link DNS-323 NAS, and were put there in Windows. The files with accented characters look like this in the terminal:

04 V? ?kur? ?.m4a

and they look like this in Nautilus:

04 V&#65533; &#65533;kur&#65533; &#65533;.m4a (invalid encoding)

This is the relevant line in my /etc/fstab:

```
//192.168.0.6/Volume_1 /media/dns_323 cifs iocharset=utf8,username=admin,password=speaker,file_mode=0777,dir_mode=0777 0 0
```Many people seem to have solved this problem by adding the iocharset part, but it isn't working for me. I also tried nls=utf8.

I've looked into using convmv to change the file name encoding, but I'm having trouble with that, too. I've read that Windows uses UTF-16, but when I try:

```
convmv -f UTF-16 -t utf8 04\ V&#65533;kur&#65533;.m4a
```I get "UTF-16:Unrecognised BOM 3034 at /usr/lib/perl/5.10/Encode.pm line 194."

I only half understand any of what I've tried to do, so I'm sorry if I'm missing something obvious. Does anybody have any suggestions?

---

### Post by tredegar on 2011-01-23
This is not my speciality, but 
> Filesystems with MS-DOS or Windows origin (i.e.: vfat, ntfs, smbfs, cifs, iso9660, udf) need the &#8220;iocharset&#8221; mount option in order for non-ASCII characters in file names to be interpreted properly. The value of this option should be the same as the character set of your locale, adjusted in such a way that the kernel understands it. This works if the relevant character set definition (found under File systems -> Native Language Support) has been compiled into the kernel or built as a module. The &#8220;codepage&#8221; option is also needed for vfat and smbfs filesystems. It should be set to the codepage number used under MS-DOS in your country.
The above came from [this page]("http://www.linuxfromscratch.org/lfs/view/6.2/chapter08/fstab.html") which you may find helpful.

---

### Post by kelsoKashka on 2011-01-23
Thanks for the reply. I hadn't seen that page before, but I'm not sure  what else I can try. I already have the iocharset in my fstab file set to utf8, which I  think is appropriate since my locale is set to en_US.utf8. Am I missing  something?

---

### Post by tredegar on 2011-01-23
> Am I missing something?
Yes, I think the **codepage** in fstab is supposed to reflect the setting of the filesystem in *windows*. I don't have win, so cannot tell you how to find that out.
See the examples (for russian) on that page

---

### Post by kelsoKashka on 2011-01-23
Okay, I've tried every combination of these that I can think of: 

iocharset=xxx,codepage=xxx

but the problem (it occurs to me I should have said this explicitly) is that the Windows machine that I used to write the files is using the standard (in America)  U.S. English, which I think is codepage 1252. So, as I understand it, the characters with the accents weren't written because of the codepage setting of the machine, but instead because of the filenames on the audio CD. I'm not sure how I can figure out which encoding the filenames use, or if they use different encodings. If I try

```
file -bi [filename]
```I get this:

audio/mp4; charset=binary

but I'm not sure if the information is helpful

---

### Post by tredegar on 2011-01-23
**file** is just telling you about the contents of the  *file*, not the encoding of the file *name* on the filesystem.

Maybe search on **linux utf-8 filename convmv accent** or subsets of these terms.

As I said, I have not used win for years, so I really can't help you further, sorry and good luck!

---

