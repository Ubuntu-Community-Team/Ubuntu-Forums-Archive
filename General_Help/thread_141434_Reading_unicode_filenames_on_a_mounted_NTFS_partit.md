---
title: "Reading unicode filenames on a mounted NTFS partition?"
date: 2006-03-08
forum: General Help
---

### Post by IYY on 2006-03-08
I have two 80 GB harddrives, one of which has Windows XP on it and the other Ubuntu. I need to copy my MP3 and lyrics collections from the XP drive to the Linux one. The problem is, I have files there with Russian and Hebrew names. By default, Linux not only doesn't display them properly, but doesn't display them at all. It's as though they don't exist.

I'm not sure what encoding Windows uses for its filenames (I think it's UTF-16), but is it possible to manage these files in Linux? I really need to make this backup, because I'm reformatting the Windows drive soon.

---

### Post by adamkane on 2006-03-08
If you mount the Windows partition, you need to add an nls=iso8859-1 flag in the /etc/fstab file. 

If you browse your Windows share rather than mount it, your files should appear in the correct encoding:

Panel -> Places -> Network Servers

If you have archives of non-UTF-8 encoded files, you will need to deal with those also. I put together some utilities to view/convert non-UTF-8 files:
convmv command, convmv Nautilus script, ROX-Filer. 

Details:
[http://www.ubuntuforums.org/showthread.php?t=139154]("http://www.ubuntuforums.org/showthread.php?t=139154")

---

### Post by IYY on 2006-03-08
Do you mind telling me exactly how to do this? If I just look in the network servers, it doesn't show anything. The only way I've been able to mount it so far was via the gnome disk manager.

---

### Post by adamkane on 2006-03-08
Is your Windows drive currently installed on a Windows machine, or is it installed as a second drive on your Ubuntu box?
[]("http://easylinux.info/wiki/Ubuntu#How_to_access_network_folders_without_mounting")

---

### Post by IYY on 2006-03-08
A second drive. I don't even have a Windows machine right now.

---

### Post by adamkane on 2006-03-08
Here is an outline of your options. I'll go into more detail according to which option you want to try:

If your Windows drive is FAT32, then you can just install the second drive, and mount it by adding this line to your /etc/fstab file:

/dev/hdb1  /media/drive2  fat32  iocharset=iso8859  0  2

If the Windows drive is NTFS, then the question is: Do you have room to move all your files onto the Linux drive? If you do, then you should install the second drive, mount it, and transfer the files from the Windows drive to your Ubuntu drive. You can then format your second drive as ext3. Add this to your /etc/fstab file:

/dev/hdb1  /media/drive2  ntfs  nls=iso8859  0  2

If you don't have room and your second drive is Windows NTFS, you'll need to format a third empty drive as Linux ext3, install all three drives, mount them, and move the files to the spare drive. Add this to your /etc/fstab file:

/dev/hdb1  /media/drive2   ext3  defaults  0  2
/dev/hdd1  /media/drive3  ntfs  nls=iso8859  0  2

Another alternative is to install your Windows drive as a second drive on a Windows machine and use browsing to transfer the files over a local network to your Ubuntu box. You can then format the second drive as ext3. Also this will only work if you have enough space on your Ubuntu drive.

There aren't any good choices, if your drive is NTFS. You'll have to find some way to free up space.

Before you do any transferring, you have to decide if you want to hold on to your ISO-8859 encodings or convert your files to UTF-8. If you want to stay ISO-8859, then you have to change the default language settings on Ubuntu.

---

### Post by IYY on 2006-03-08
Yes, I have space for it.

I like this option:

> If you do, then you should install the second drive, mount it and transfer the files from the Windows drive to your Ubuntu drive, then convert the files.

But the question is: will the conversion really allow me to keep the non-english characters in the filenames?

---

### Post by adamkane on 2006-03-08
I edited my earlier posts, you probably won't need to convert anything, if we do this right. Adding nls=iso8859 to your /etc/fstab file will allow you to see your encodings. I'll show you how to convert, if it is necessary.

The following assumes you've installed the second drive as a primary slave. You will need to create a folder called /media/drive2 or something similar, and adjust the permissions of the new folder.

```

sudo mkdir /media/drive2
sudo chmod 744 /media/drive2

``` 
Open your /etc/fstab file for editing:

```

sudo gedit /etc/fstab

``` 
Edit the /etc/fstab file, so that /dev/hda1 and /dev/hdb1 look like this:

    /dev/hda1  /                    ext3  errors=remount-ro  0  1
    /dev/hdb1  /media/drive2  ntfs  nls=iso8859  0  2

Remount your drives:

```

sudo mount -a

``` 
Copy a few files from /media/drive2 to /home/<username> to make sure everything is OK.

After you've transferred all the files off the Windows drive, then use gparted to format your second drive as ext3.

---

### Post by IYY on 2006-03-09
>  sudo mount -a

On this step, it says:

> 
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I thought it could be a good idea to try with /dev/hdb instead of /dev/hdb1 but it also gives an error:

> mount: /dev/hdb already mounted or /media/drive2 busy


---

### Post by adamkane on 2006-03-09
Typo. Add this to fstab:

/dev/hdb1  /media/drive2  ntfs  nls=iso8859-1  0  2

Then try this again:
```

sudo mount -a

```

hdb1 refers to the first partition on harddrive b. hdb refers to the harddrive itself.

---

### Post by IYY on 2006-03-09
This seems to do the same thing as mounting it from the disk manager: I still can't see the files that are in non-english characters. It's as though they are not there at all.

---

### Post by adamkane on 2006-03-09
Try this:

/dev/hdb1  /media/drive2  ntfs  nls=cp850  0  2

Then this again:

```

[LEFT]sudo mount -a[/LEFT]
  
```
 
Just want to try this, then I'll show you how to convert the file names.

---

### Post by IYY on 2006-03-09
I did that, but I still can't see the files.

---

### Post by adamkane on 2006-03-09
Another one to try is nls=CP1252. Sorry for the difficulties. I'm learning as well.

But at this point, you should try some conversion. Keep a copy of all your files on the Windows drive, until you are sure that the files have all been converted. The only risk is that you will double-convert some of your files, and you won't know which ones have been double-converted and which ones haven't been converted at all.

Copy a small folder of files to the Linux drive and do a test conversion. The following will convert all the files in a folder and any subfolders.

```

cd /<path to files to convert>
convmv -f **cp850** -t utf-8 -r --notest *.*

``` 
There is also a Nautilus script that you can install, that will allow you to right-click any folders you want to convert. Let me know if you want to try the Nautilus script.

Here is a list of all the possible encodings to try with nls=

> 
[SIZE=1] 7bit-jis AdobeStandardEncoding AdobeSymbol AdobeZdingbat ascii ascii-ctrl big5-eten big5-hkscs 
cp1006 cp1026 cp1047 cp1250 cp1251 cp1252 cp1253 cp1254 cp1255 cp1256 cp1257 cp1258 cp37 cp424 cp437 cp500 cp737 cp775 cp850 cp852 cp855 cp856 cp857 cp860 cp861 cp862 cp863 cp864 cp865 cp866 cp869 cp874 cp875 cp932 cp936 cp949 cp950 
dingbats euc-cn euc-jp euc-kr gb12345-raw gb2312-raw gsm0338 hp-roman8 hz 
iso-2022-jp iso-2022-jp-1 iso-2022-kr iso-8859-1 iso-8859-10 iso-8859-11 iso-8859-13 iso-8859-14 iso-8859-15 iso-8859-16 iso-8859-2 iso-8859-3 iso-8859-4 iso-8859-5 iso-8859-6 iso-8859-7 iso-8859-8 iso-8859-9 iso-ir-165 
jis0201-raw jis0208-raw jis0212-raw johab koi8-f koi8-r koi8-u ksc5601-raw 
MacArabic MacCentralEurRoman MacChineseSimp MacChineseTrad MacCroatian MacCyrillic MacDingbats MacFarsi MacGreek MacHebrew MacIcelandic MacJapanese MacKorean MacRoman MacRomanian MacRumanian MacSami MacSymbol MacThai MacTurkish MacUkrainian 
MIME-B MIME-Header MIME-Q nextstep null posix-bc shiftjis symbol UCS-2BE UCS-2LE 
UTF-16 UTF-16BE UTF-16LE UTF-32 UTF-32BE UTF-32LE UTF-7 utf-8-strict utf8 viscii

[/SIZE]

---

### Post by adamkane on 2006-03-09
I did some more reading:
[http://www.gentoo.org/doc/en/utf-8.xml](http://www.gentoo.org/doc/en/utf-8.xml)

You may have to add this to /etc/fstab:

/dev/hdb1  /media/drive2  ntfs  nls=utf8  0  2

Then this again:

```

sudo mount -a

```

---

### Post by IYY on 2006-03-10
Ok, this works. I see the files now, and they are named correctly.

---

### Post by adamkane on 2006-03-10
Yes!

---

### Post by IYY on 2006-03-10
Thanks for the help, man!

Now, what is **convmv** for?

And, is it also possible to convert song information inside the files (things like track title, artist)?

---

### Post by adamkane on 2006-03-10
You'll still be able to view your old ID3 tags. Most MP3 players and music managers assume you have ISO-8859-1 ID3 tags, and will display the ID3 tags correctly. As time goes by, more music managers will allow you to save ID3 tags in UTF8. I don't think it is an issure for most people yet.

I would like to be able to save my ID3 tags in UTF-8, but I haven't found anything except gtkpod. gtkpod is good at reading files on your ipod, but it's difficult to use as a music manager/ID3 tag editor.
[http://gtkpod.sourceforge.net/documentation/html/preferences.html]("http://gtkpod.sourceforge.net/documentation/html/preferences.html")

Info about beep-media-player, similar to Winamp.
[http://bmp.beep-media-player.org/index.php/FAQ#Why_do_I_have_.22.3F.3F.3F_.28Invalid_UTF-8.29.22_in_the_playlist.3F]("http://bmp.beep-media-player.org/index.php/FAQ#Why_do_I_have_.22.3F.3F.3F_.28Invalid_UTF-8.29.22_in_the_playlist.3F")

My understanding is that EasyTag will save your ID3 tags in UTF-8, if you use it to do any editing.

There are probably scripts out there to convert ID3 tags, but I haven't found any yet.

---

