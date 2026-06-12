---
title: "lost+found"
date: 2012-05-30
forum: General Help
---

### Post by SuperFreak on 2012-05-30
I have a internal hard drive (ext 4) where permissions were changed and I notice that lost+found permissions may have changed as owner and group is me rather than root. Is this a problem and is there a way of correcting it? Here is output of ls- l :

```
david@david-desktop:~$ cd /media/STORAGE
david@david-desktop:/media/STORAGE$ ls -l
total 40
drwxrwx---  4 david david  4096 May  6 08:39 Documents
drwxrwx---  4 david david  4096 May 29 21:22 Downloads
drwxrwx---  2 david david 16384 May  4 09:39 lost+found
drwxrwxr-x  3 david david  4096 May  6 08:39 Music
drwxrwx---  3 david david  4096 Jan 17  2009 My RoboForm Data
drwxrwx---  7 david david  4096 May  6 08:40 Pictures
drwxrwx--- 12 david david  4096 May  6 08:40 Videos
david@david-desktop:/media/STORAGE$ 


```

---

### Post by oklokl on 2012-05-30
Doing so.. How about this way?
In my case, this is used.

Nautilus folder active partition
sudo chown -Rh david /media/STORAGE  && sudo chown -Rh root /media/STORAGE/lost+found

Please try it twice.


david -> user
STORAGE -> Partition

---

### Post by SuperFreak on 2012-05-30
I don't want to change permissions of the directory Storage because that may affect other directories within, just the Lost+Found directory. I haven't done anything yet but would 

```
sudo chown -Rh root /media/STORAGE/lost+found

```

achieve that?

---

### Post by oklokl on 2012-05-30
The default is the root
lost+found


sudo chown -Rh david /media/STORAGE
en bloc -> Change batch
 lost+found -> The default value is changed.


Please advise if you have any other way.

 I'm looking ..

---

### Post by SuperFreak on 2012-05-30
I am a little out of my depth here. The Storage partition is not in Home but a separate hard Drive containing data. I already had a mess changing permissions on this drive (which has been fixed) and am hesitant to do it again. I was hoping to just fix the one folder Lost+Found if my assumption is correct that it should be a locked root folder (even though it is located outside of root and home.

---

### Post by oklokl on 2012-05-30
I understand.
Sorry not to help.

---

### Post by bab1 on 2012-05-30
> **SuperFreak said:**
> I am a little out of my depth here. The Storage partition is not in Home but a separate hard Drive containing data. I already had a mess changing permissions on this drive (which has been fixed) and am hesitant to do it again. I was hoping to just fix the one folder Lost+Found if my assumption is correct that it should be a locked root folder (even though it is located outside of root and home.

You can change the owner:group using chown.  The command would be```
sudo chown -R **[COLOR="Red"]root:root[/COLOR]** /media/STORAGE/lost+found
```

If you want to try it you can create a directory structure (i.e. ~/test1 and subdirectories) and chown that to root:root.  That is: *root* is owner and the* group root* is the group.

Since you can use sudo you can also reverse this.  why are you using -h with chown.  There should be no symlinks and therefore no need for -h.

---

### Post by uylug on 2012-05-30
> **bab1 said:**
> The command would be```
sudo chown -R **[COLOR=Red]root:root[/COLOR]** /media/STORAGE/lost+found
```

^^This is the command you should run.

I don't really get why you're so worried about this. Root will still be able to alter the lost+found folder so no big deal, really.

---

### Post by bab1 on 2012-05-30
> **uylug said:**
> ^^This is the command you should run.

I don't really get why you're so worried about this. Root will still be able to alter the lost+found folder so no big deal, really.

Because he asked.  This is a learning moment for OP.

---

### Post by SuperFreak on 2012-05-30
@bab1

Greatly appreciate your help, worked as I had hoped it would. 
Yes I am learning how permissions work. I know there are Man pages and other guides but working directly on my system seems more helpful.

---

### Post by bab1 on 2012-05-30
> **SuperFreak said:**
> @bab1

Greatly appreciate your help, worked as I had hoped it would. 
Yes I am learning how permissions work. I know there are Man pages and other guides but working directly on my system seems more helpful.

You really shuld read the man pages and google the terms.  That way you can learn not only how but why you use these commands.

Glad  could help in this instance.

---

