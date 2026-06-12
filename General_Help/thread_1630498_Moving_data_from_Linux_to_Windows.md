---
title: "Moving data from Linux to Windows"
date: 2010-11-25
forum: General Help
---

### Post by yme on 2010-11-25
One of the reasons I started to give Ubuntu a go a few years back was because it was sold to me as compatible with Windows. I thought that if I don't like it, I can give up and go back to Windows any time I want. Seems not!

After a couple of years using Linux I wanted to share some of my saved research with a colleague. This is an archive of mostly .pdf and .doc files that is about six gigabytes. 

I tried to transfer and straight away started getting error messages saying that the Linux filename was not valid in Windows. I have complained about this several times and been told that in later versions this would be sorted. I installed 10.10 today and, guess what, nothing has changed!

How difficult can it be for someone to set up the system so that instead of giving an error message and suggesting 'skip', it offers to change the file name to one that will work with Windows?

---

### Post by searchfgold6789 on 2010-11-25
By what method are you sharing the files?
If you are doing so by  a network, then I would recommend instead copying the files to a series of CD's, DVD's, or internet resources and then moving the files to his computer.

---

### Post by a-user on 2010-11-25
i have no clue what problems you have. ubuntu supports by default ntfs filesystems. so mounting a windows partition and copieng your files to it is cheesy easy.

and if you want, there are ext2/3-reader programs with that you can read a ext2 or ext3 partition. newer ones support ext4 (but as far as i know only reading). so you can copy them from windows too.

---

### Post by rusty149 on 2010-11-25
You could filter the disallowed filenames and modify then either in a script or through commands. 
 
For example: 
```
ls /home/user | grep " * : < > ? \ 
```
That should list filenames with illegal characters. (Change the path to the folder you are copying)
Are there other reasons they are being blocked?

---

### Post by mastablasta on 2010-11-25
if special characters are the issue how is this a linux fault? it's windows that doesn't know how to read them in file name.

---

### Post by alexee on 2010-11-25
> **searchfgold6789 said:**
> By what method are you sharing the files?

I am just copying them to a FAT32 memory stick. I don't want to mess with CDs. They are too small and in my experience always manage to get damaged no matter how carefully you treat them.

> **Irony said:**
> How terrible for you.

Well, yes. I have several years work which I can't share with anyone. It is pretty terrible as I have waited several months to get 10.10 in the hope that would fix it. It is a pretty major error not to have compatibility between file names.

> **mastablasta said:**
> if special characters are the issue how is this a linux fault? it's windows that doesn't know how to read them in file name.

I live in Brussels. I just went into the bakery and asked the lady for a baguette in English. When she couldn't reply to me in English I told her it was her fault. 

I'm not sure why I have had such aggressive and hostile responses. This isn't the Church of Ubuntu so I presume we are allowed to mention it has faults without being burnt as heretics. I am grateful to the people who made positive and constructive replies.

> **rusty149 said:**
> You could filter the disallowed filenames and modify then either in a script or through commands. 
 
For example: 
```
ls /home/user | grep " * : < > ? \ 
```That should list filenames with illegal characters. (Change the path to the folder you are copying)
Are there other reasons they are being blocked?

It simply comes down to the fact that Ubuntu allows a lot of characters that Windows does not.

I guess if I have this list I can go and change them all manually. But are you sure that " * : < > ? \ are the only noncompatible characters? I have a feeling there are more.

---

### Post by Vaphell on 2010-11-25
> Well, yes. I have several years work which I can't share with anyone. It is pretty terrible as I have waited several months to get 10.10 in the hope that would fix it. It is a pretty major error not to have compatibility between file names.

The problem is that you expect too much from the community that works largely for free. If you have some itch, sometimes you have to scratch it yourself - google and a bit of reading is all you need, really. There are examples of scripts to automate tackling such problems, there are also tools that can for example convert names between encodings (another issue you can meet: win12xx of windows vs utf8 in ubuntu) 
Community time is better spent elsewhere, so we can have a better system overall, not a more-compatible-with-windows one.

> PS. Why are people so aggressive about Ubuntu's shortcomings? I am grateful to the people who made positive and constructive replies.

people are 'aggressive' about impying that it's a shortcoming when it's not really a shortcoming. Besides, even if we assume it is, windows by the same metric has many more shortcomings in terms of interoperability
- linux can use ntfs, windows can't use extX
- linux can set up dual boot without making other OSes unusable, windows wipes everything in bootsector
- linux can run some win binaries in wine, windows can't run linux binaries at all

when your ipod just works thanks to native itunes in windows and mac and you have to jump through the hoops to make it to work in linux, do you blame linux for being left out in the cold or Apple that intentionally made the decision? Microsoft similarly doesn't put any effort to provide any interoperability with non-MS systems so why should linux be flamed for not being quite there yet?

---

### Post by WorMzy on 2010-11-25
> **alexee said:**
> I live in Brussels. I just went into the bakery and asked the lady for a baguette in English. When she couldn't reply to me in English I told her it was her fault.

If I write a book in English, is it my fault if someone in China cannot read it? No. Is it their fault? Not really, but if they want to read the book then I don't see why it's my duty to translate it for them. I certainly don't see why I should write any future books in a way that they can understand.

According to [wikipaedia]("http://en.wikipedia.org/wiki/Comparison_of_file_systems"), NTFS supports any Unicode characters except NUL \ / : * ? " < > |

Remove those characters from your filenames.

---

### Post by aeiah on 2010-11-25
this is a limitation with the FAT32 file system, not with linux nor with windows. whoever told you it would be fixed in future versions is either wrong, or you misunderstood.

FAT32 is 15 years old and has many limitations, such as a 2GB file size, and directory tree length etc, as well as character limitations. 

Format your usb stick as NTFS and try it with that, or give us examples of when this error occurs (such as real file names) etc and we'll see if it can be fixed with a bash script or something.

---

### Post by searchfgold6789 on 2010-11-25
You will probably have to remove the said characters from the filenames, using the command given to you.
Be careful if you format your USB stick. Flash drives only support FAT 100%.

---

### Post by aeiah on 2010-11-25
> **searchfgold6789 said:**
> Flash drives only support FAT 100%.

citation needed please. ive treated them like a normal hdd for the past 8 years.

---

### Post by a-user on 2010-11-25
it does not matter what fs you use for flash drives.
there only might be a difference for flash drives that do some kind of self trimming. this works only if they can "understand" the filesystem in use. such flash drives usually only support this funciton with fat or ntfs (it is a commerical thing).

but they are still 100% working with ANY other fs. only this special feature might be not working which can temporary decrease the performance under special situations. but most flash drives (usb sticks) don't have this feature anyway.

---

### Post by yme on 2010-11-26
> **Vaphell said:**
> Community time is better spent elsewhere, so we can have a better system overall, not a more-compatible-with-windows one.

when your ipod just works thanks to native itunes in windows and mac and you have to jump through the hoops to make it to work in linux, do you blame linux for being left out in the cold or Apple that intentionally made the decision? Microsoft similarly doesn't put any effort to provide any interoperability with non-MS systems so why should linux be flamed for not being quite there yet?

I think this reply and that of Wormzy show a hugely problematic attitude with many Ubuntu users. Compatibility has to be one of the most important things. You can't pretend that 90% of the world does not use Windows. 

If it was the other way round, OK I can be arrogant and pretend it is the other guy's problem but when I have decided to use a different system to most people, I do think it is not an unreasonable expection that it has to be me that fits in with my colleagues not the other way round. 

I must say looking at the new 10.10 it seems to be full of gimmicky features for people who spend too much time on Facebook. Basic issues like compatiblity and the ability to export work should come way ahead of it.

As it is my colleagues have been laughing for months at my difficulties in sharing and backing-up my work. It really isn't a good advertisement for Ubuntu!

---

### Post by yme on 2010-11-26
> **aeiah said:**
> Format your usb stick as NTFS and try it with that, or give us examples of when this error occurs (such as real file names) etc and we'll see if it can be fixed with a bash script or something.

I want to backup to a FAT system at work as well so really need to sort the issue with the characters. The problem comes in that there are lots of academic papers which have been saved with the exact title which often includes : or ? and maye some other illegal characters.

---

### Post by Vaphell on 2010-11-26
> I think this reply and that of Wormzy show a hugely problematic attitude with many Ubuntu users. Compatibility has to be one of the most important things. You can't pretend that 90% of the world does not use Windows.

If it was the other way round, OK I can be arrogant and pretend it is the other guy's problem but when I have decided to use a different system to most people, I do think it is not an unreasonable expection that it has to be me that fits in with my colleagues not the other way round.

I must say looking at the new 10.10 it seems to be full of gimmicky features for people who spend too much time on Facebook. Basic issues like compatiblity and the ability to export work should come way ahead of it.

As it is my colleagues have been laughing for months at my difficulties in sharing and backing-up my work. It really isn't a good advertisement for Ubuntu!

There is nothing particularly wrong with my attitude, i help people who want to learn every day. Many things in linux or in ubuntu in particular **** me off, but compatibility is already just fine. You can mount windows partitions after all and manipulate data there, out of the box - how cool is that?!

But you can also make your life easier by simply not using oddball or language specific characters. Encodings and naming conventions vary across platforms and filesystems and that's the fact of life. To accomplish your goal of interoperability you need few hours of google and learning, that's all. If that's too much then maybe linux is not for you. I am not an elitist here - you having a poor experience with linux means you get disappointed, you tell your friends that linux sucks => linux reputation is hurt and its adoption is slowed and i don't want that.
You need to be mentally ready to drop old habits and to learn new stuff, otherwise you are doomed to fail. There are plenty of tools but you need to do your homework and investigate, not whine that ubuntu is less compatible with windows than windows.
Linux requires some level of computer literacy, computers that Just Work are called macs and cost a ton.

---

### Post by deserthowler on 2010-11-26
I have had no problems.  I use NTFS as the filesystem on my USB drive ... it came with that.
With the problems you are having, you should probably be using Windows.

Earl

---

### Post by matt_symes on 2010-11-26
Hi

> Flash drives only support FAT 100%.

Rubbish

Kind regards

---

### Post by pycoed on 2010-11-26
YME, 
I've only been using Ubuntu for 6 months, but in that time I've been amazed at how many ludicrous complaints like this I've seen on these forums. 
YOU have complete control over naming files which YOU know YOU need to share with Windows yet YOU have chosen to use "ineligible" characters in those file names. By some twisted logic you impute this as a problem with Ubuntu!! Rather than a forum, I suggest you use a mirror to identify the root of the problem.:D

---

### Post by WorMzy on 2010-11-26
> **matt_symes said:**
> Hi

> Flash drives only support FAT 100%.

Rubbish

Kind regards

I lol'd. But I agree.

There are certain features, like encryption, which some flash drives come with which may only work with the filesystems they come with, but these features are generally designed for Windows OSs rather than Linux/Mac OSs.

@ yme: You might think that my attitude is "hugely problematic", but I maintain that Linux shouldn't be held back by the shortcomings of Windows. Linux-based OS' are far superior to Windows OS' in almost every regard (imho). This is not a shortcoming on the Linux side of things, but rather a shortcoming on the Windows side of things.

Look at it this way: Games created for Windows do not work that well on Linux, even with the wine compatibility layer -- *this* is a shortcoming of the Linux-based operating systems, but at least Linux can *run* Windows applications. Linux, as a community, is trying to appease *everyone*, be they be a Windows user, Mac user, or Linux user. If you're unhappy that the ext4 filesystem supports more characters than the NTFS or FAT filesystems, then go ahead and write your own filesytem that A) supports Linux file permissions/ownership and b) is compatible with Windows filesystems. Nobody is going to turn around and say "Oh yes, we're sorry that our filesystems don't have the same restrictions as Windows filesystems do" because nobody *is* sorry. The fact that you have file names with "illegal" characters is due to the fact that Linux offers you more freedom. If you want to keep your filenames compatible with Windows, then that's up to you, not everyone else; if you can't cope with that, then go back to Windows.

---

### Post by deserthowler on 2010-11-26
Two things to remember in the compatibility issue:
1> Linux is trying to be compatible to Windows
2> Windows is trying to be incompatible to Linux

This explains a lot of the "short comings" of Linux.

Earl

---

### Post by yme on 2011-04-07
Can anyone help me here? I'm still stuck with three years of unbacked up work. Makes me very nervous and I keep hoping the issue will be dealt with in upgrades but it never is. 

My university's computer unit won't give me any help at all. Says it is my fault for using Linux in the first place ...

---

### Post by Mark Phelps on 2011-04-07
> **yme said:**
> Can anyone help me here? I'm still stuck with three years of unbacked up work. Makes me very nervous and I keep hoping the issue will be dealt with in upgrades but it never is. 

My university's computer unit won't give me any help at all. Says it is my fault for using Linux in the first place ...

It's generally a simple matter to plugin an external drive (or USB stick), copy the files onto that media, plug it into a Windows PC, and copy the files there.

Of course, any files created to work with Linux apps will most likely NOT work with Windows apps, unless there is a version of the app built for Windows.

If it's more complicated than this, please start your own thread -- and provide us some details so we know what we're dealing with.

---

### Post by jerome1232 on 2011-04-07
So the problem: ext4 allows characters that fat16/32 doesn't

Your files have characters that aren't allow in fatt16/32.

Solution: Batch rename your files, I was trying to hit up google to find a suitable script but couldn't find one in the 15 minutes I had to search. Maybe someone can help you either A) create a sutible batch script, or B) Find one else where. 


I would make sure to make two copies of your data and run the script one ONE copy to prevent accidental file loss.

---

### Post by SecretCode on 2011-04-07
> **yme said:**
> Can anyone help me here? I'm still stuck with three years of unbacked up work.

How much data? Did you say about 6GB?

One approach would be to get a USB stick that's large enough and format it to ext3/4. Then you should be able to copy all your data to it as a backup (not yet addressing how you can read this data on Windows). (Three years of data is definitely worth buying some extra memory sticks and/or drives.)

Another might be to get hold of Truecrypt for Linux, and create an ext3 volume. You should then be able to copy all your existing files into the volume. Again as a backup, encryption is not the point.

> **yme said:**
> Makes me very nervous and I keep hoping the issue will be dealt with in upgrades but it never is. 

I don't think this issue will ever be "fixed" in upgrades - it's because of "features" of the different file systems, not bugs.

---

To be able to read the file with NTFS-unsupported characters in, you will **have** to rename them. Do you have an idea how many of the files have unsupported names?

---

### Post by idoitprone on 2011-04-08
Let see how bad is the damage

```
ls -Ra /parent/directory/of/your/stuff | grep ['* : < > ? \ ']

```If i miss an illegal character, add in any other characters you can think of.

```
tree -l /media/filename?/ | sed -e '$d' -e 's/.* //g' | uniq -i -d
```this is case-sensitive test.

You have to install tree

Note I want to use ls -R, but directory are listed with a semi-colon and I wanted to test directories against normal files

---

### Post by Duncan Williams on 2011-04-08
you can access windows files from ubuntu.
copy them as is to a usb stick or dvd. and you can then retrieve them via linux or windows?

---

### Post by idoitprone on 2011-04-08
> **Duncan Williams said:**
> you can access windows files from ubuntu.
copy them as is to a usb stick or dvd. and you can then retrieve them via linux or windows?
 

i dont think that is op problem. His problem is transferring files from Ubuntu to windows.
Even if he has a compatible driver for ext2 and ext3, he has to rename the files to to support windows file system limited capability of handling special characters. For the most part windows do not have support for linux file systems

---

### Post by SecretCode on 2011-04-08
I prefer **find**:

```
find /home/wherever -regex ".*[\"\:*?<>].*" | less
```

The / character is illegal in NTFS filenames (see [http://msdn.microsoft.com/en-us/library/Aa365247](http://msdn.microsoft.com/en-us/library/Aa365247)) but it's unlikely a Linux user would create such a file either! The same applies to "control" characters 0x1 to 0x1a.

Single quotes are legal but double quotes are not.

---

### Post by Duncan Williams on 2011-04-08
What about linux_reader.
[http://www.download25.com/diskinternals-linux-reader-download.html](http://www.download25.com/diskinternals-linux-reader-download.html)

---

### Post by Buntumatic on 2011-04-08
Incredible. How can there be so much fuss about nothing? There is  probably a hundred ways how to transfer those files. How about letting  them download it from your box over SSH. Or FTP. Or just upload files to  some FTP server and let them download from there. 
Network is always my first choice if I need to transfer files. That said, my last Windows died in 2003 ...

---

### Post by idoitprone on 2011-04-11
> **Buntumatic said:**
> Incredible. How can there be so much fuss about nothing? There is  probably a hundred ways how to transfer those files. How about letting  them download it from your box over SSH. Or FTP. Or just upload files to  some FTP server and let them download from there. 
Network is always my first choice if I need to transfer files. That said, my last Windows died in 2003 ...

I think you should read the post better, most of the fuss is correct other people fuss, fuss about microsoft, or improve fuss like makeing a script to diagonosis the fuss. Lol, i wrote fuss 5 times.

> After a couple of years using Linux I wanted to share some of my saved  research with a colleague. This is an archive of mostly .pdf and .doc  files that is about six gigabytes. .... Linux filename was not valid in WindowsThe main problem is cross-platform compatibility, he reach a limitation of the ntfs file system.  So of course he will receive lots of reception. Buntumatic, I dont think your method will work since the op will still have to rename the file either way as ntfs support less characters than linux. What you are recommend is downloading through a server, but if the file touches ntfs file system, things can go wrong

---

### Post by yme on 2011-05-13
Jerome has hit the nail on the head. What I need to do is 'batch rename'. 

Indeed, what I just cannot understand is why Ubuntu does not automatically ask me if I want to rename a file which has invalid characters when I try to transfer an invalid file to a FAT system. If you try to save a file using invalid characters in Windows it won't do it but offers instead the name you wanted minus the invalid characters.

Or at the very least it could give me a list and I could go through and manually rename. That would be a pain but not as big a pain as not being able to share my archive. Idiot's idea is OK but prone to ****-up as one of the later posters points out, you have to know all those characters. I certainly don't and he missed at least one out himself. It is not a fool proof way.

---

### Post by SecretCode on 2011-05-13
It turns out - not that it's any use to you now - that the ntfs-3g driver has an option to limit to legal windows file names. But it's not the default. You could certainly argue that it should be!

[ntfs-3g(8**) - Linux man page](http://linux.die.net/man/8/ntfs-3g)

> Windows Filename Compatibility
NTFS supports several filename namespaces: DOS, Win32 and POSIX. While the ntfs-3g driver handles all of them, it always creates new files in the POSIX namespace for maximum portability and interoperability reasons. This means that filenames are case sensitive and all characters are allowed except '/' and '\0'. This is perfectly legal on Windows, though some application may get confused. If you find so then please report it to the developer of the relevant Windows software. 

(good luck reporting anything to Microsoft)

That's obviously not talking about the latest version of ntfs-3g, because on my Ubuntu 10.10 system, it says

>    Windows Filename Compatibility
       NTFS supports several filename namespaces: DOS, Win32 and POSIX.  While
       the  ntfs-3g driver handles all of them, it always creates new files in
       the POSIX namespace for maximum portability and  interoperability  rea&#8208;
       sons.   This means that filenames are case sensitive and all characters
       are allowed except '/' and '\0'. This is perfectly  legal  on  Windows,
       though  some application may get confused. The option windows_names may
       be used to apply Windows restrictions to new file names.

and

>        windows_names
              This  option prevents files, directories and extended attributes
              to be created with a name not allowed by windows, either because
              it contains some not allowed character (which are the nine char&#8208;
              acters " * / : < > ? \ | and those whose code is less than 0x20)
              or because the last character is a space or a dot. Existing such
              files can still be read (and renamed).


---

### Post by jerome1232 on 2011-05-13
Holy old Ubuntu beans batman,

Are you really using 7.04 still?

---

### Post by Thewhistlingwind on 2011-05-13
> **Vaphell said:**
> 
- linux can run some win binaries in wine, windows can't run linux binaries at all



 Correction, Cygwin, nuff said.

([http://en.wikipedia.org/wiki/Cygwin](http://en.wikipedia.org/wiki/Cygwin))

Also, renaming the files so that they don't have illegal characters (Google can give you a list.) SHOULD solve your problem.

> **yme said:**
> Jerome has hit the nail on the head. What I need to do is 'batch rename'. 


YOU'VE HAD THIS PROBLEM UNSOLVED SINCE 2010!!!!????

---

### Post by col48 on 2011-05-13
Moving files between different Windows systems can be a pain, too.  But that would be for another forum!  You get much more FREE help from the smaller Linux community than the commercial Windows one.

---

### Post by col48 on 2011-05-13
If it were me, being cautious and not very familiar with shell commands, I would 

1. assemble a list of the files with Windows-illegal names
2. make a copy of them somewhere well away from the originals
3. build a batch file which would rename the copied files one by one (build it using a spreadsheet)
4. eyeball the batch to check the names are sensible
5. run the batch
6. make notes on the whole process so I could do it again in future

---

### Post by yme on 2011-05-18
Secretcode is quite right. The default should be set so you can't accidentally save files with non-compatible files names. Is there any way to contact the developers with these suggestions?

And, yes I have had this problem for eighteen months. I ended up buying a new harddrive and have that as FAT using Ubuntu so I can at least back up more recent work. But it is very difficult working with two different file systems and there is also the risk of loss of work by overwriting newer files with older versions. 

Col's suggestion depends on me being 100% certain I can make my own script. I had a go in the past but on such an important matter there is a good chance of buggering it up. I can risk it when it is something stupid to do with listening to music or watching films but not with my backup. 

In any case, the process of file transfer is so badly thought out that it doesn't even output a list of the dodgy filenames so I can't even complete his step one.

---

### Post by YesWeCan on 2011-05-18
Windows and linux are not fully compatible, end of story.

You have enjoyed being able to use a full set of characters in file names in linux (except $ which can cause linux some problems). Windows does not support them. You didnt realize this.

6GB is not a lot of data these days. You should duplicate them, in linux, as a backup and then run a shell script to strip the Windows-forbidden charaters out of the filenames. And try to avoid copying them to FAT because you may encounter filename length restrictions.

I think if you stop bashing linux a kind member will provide you with a bash script if you ask nicely. :p

---

### Post by col48 on 2011-05-18
yme makes some good points.  We are all dependent on our own particular knowledge and experience.  I am not totally confident of my skill in building batches, but I do know how to rename a single file in Terminal and how to execute a batch and would start from there.  Others are at home with all the weird variety of wildcards.

As for the specific points, this is how I would approach them...
1. names which are wholly alphanumeric apart from a single '.', start with a letter and have an extension of no more than three characters (the extension being all the text after the '.') and are of reasonable length (say up to 35 characters) will definitely be legal in Windows.  [So will many others, of course].  So I would include all other names in the list of illegals.  I'd also have a convention which would ensure that if two files had names which were identical except for Upper/Lower case, one would be on the list - this would depend on my habitual way of naming files.

I think I'd start with a list of ALL files and eliminate the definitely legal ones.

2. Part of the point of working with copies of the original files is to spot the unforeseen if disaster stikes some of the files.  I didn't include this in the list I made, but copy rather than rename the files, and check the same number of files emerge as went in.


This exercise is time-consuming.  So I think I'd learn to be more conservative in future when naming files!  Assuming I wanted to maintain compatability.....

---

### Post by jmore9 on 2011-05-18
All my partitions are NTFS , i use them in ubuntu for file storage and whatever.  The only native linux is the one with the Ubuntu install.  I just mount the ntfs's and share with the windows machines via cross over cable.  Ubuntu 10.10 uses NTFS with no problems now so with 2 windows machines needing access to files on this linux machine i just use one file system for both.

---

### Post by Asmodai on 2011-05-18
I seriously don't see what everyone is going on about.
The correct answer has been posted long ago: stop using legacy FAT32 and use NTFS.
NTFS supports file names with < > ? etc. just fine and there are no problems copying files containing these characters over to NTFS.
Even so, there should be no problems copying files to FAT32 either - illegal characters are automatically replaced with _ during copying, so what's the problem?

---

### Post by SecretCode on 2011-05-18
> **Asmodai said:**
> NTFS supports file names with < > ? etc. just fine and there are no problems copying files containing these characters over to NTFS.
Even so, there should be no problems copying files to FAT32 either - illegal characters are automatically replaced with _ during copying, so what's the problem?

That's incorrect. Have you tried it? I have. With the ntfs-3g driver you can easily create filenames on an NTFS drive containing : and other characters. **These files cannot be read on Windows XP or Windows 7.** (You can see them in a directory listing but an attempt to open them results in a "file not found" error.)

I am not at my home computer now and I don't have the list of files I tried, but < > * etc are **not** valid.

---

