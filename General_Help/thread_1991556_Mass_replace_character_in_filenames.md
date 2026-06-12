---
title: "Mass replace character in filenames"
date: 2012-05-30
forum: General Help
---

### Post by Erik1984 on 2012-05-30
Hi Ubuntuforums,

I dual boot Kubuntu 11.10 with Windows7 and I ran into trouble with Windows' backup function. Kubuntu and W7 share a NTFS datapartition where I store documents, music etc. When I tried to make a backup of the music folder it trips over some directories. After some trial and error I guess I found the problem: file names containing characters that are not allowed in Windows, like ":" but don't cause trouble on Linux. 

tl;dr: I want to change all occurrences of ":" to "-" in file and folder names under a certain directory, in this case my music folder. Guess it should be easy with a little bash scripting but I don't know exactly how.

---

### Post by PeterP24 on 2012-05-30
I use PyRenamer for that sort of stuff ... It has a tab Insert/Delete characters in the name of the files. I never used it in a way that implied the deletion or changing the original files though.

---

### Post by papibe on 2012-05-30
+1 for pyRenamer. Very useful and easy to use.

If you want to go old school, you can use the 'rename' command to replace  all ':' with '-' from the filenames:
```
rename 's/:/-/g' *
```
Regards.

---

### Post by Rebelli0us on 2012-05-30
I have the same problem:

[http://ubuntuforums.org/showpost.php?p=11879903&postcount=19]("http://ubuntuforums.org/showpost.php?p=11879903&postcount=19")

it's illegal characters **and** unicode filenames that many apps cannot display.

---

### Post by Vaphell on 2012-05-31
try convmv
it converts names from <encoding> to <encoding>

---

### Post by coffeecat on 2012-05-31
@Euroman, just to emphasise a matter mentioned in the link that Rebelli0us posted which you might like to consider. If you use the "windows_names" mount option in your /etc/fstab line, that will prevent you from saving files with illegal characters - illegal for Windows that is. (By the way, windows_names, not windows_name.)

It's interesting that you mention files in your Music folder. I've come across this problem with purchased and downloaded mp3 albums - some of the tracks in the occasional album contained illegal characters in the filename such as ':' and I only noticed this when copying the files to a SMB share in my NAS - the filenames became garbled. I find that quite surprising as I would have thought that most customers of the online store where I bought the MP3s would be using Windows and would have as much trouble saving to NTFS as I did copying to a SMB share.

---

### Post by Erik1984 on 2012-05-31
Thank you all for the insightful responses. I was unaware of the windows_names option for fstab. If I add that option, what happens to files and folders already containing illegal characters?

@coffeecat 
I was surprised too. Those 'illegal names' are caused by K3B pulling data from CDDB (which I guess is also used by Windows apps). One example of such an album title is "blur: the best of". This is just the official title as it also appears that way on the physical cover. I wonder how Windows Media Player handles this.

---

### Post by coffeecat on 2012-05-31
> **Euroman said:**
> If I add that option, what happens to files and folders already containing illegal characters?

It will only prevent you saving files with illegal characters in the filename to the mounted NTFS partition. You'd still need to rename already saved files.

---

### Post by Erik1984 on 2012-06-11
Forgot about this thread, but I still have a question:

If the "windows_names" option is enabled and I rip an album to the NTFS partition that contains illegal characters in the filenames I will get an error? So I guess it's safer then to first rip to my ext4 partition and copy the album over to see if the names are okay.

---

