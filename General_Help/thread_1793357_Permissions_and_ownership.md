---
title: "Permissions and ownership"
date: 2011-06-29
forum: General Help
---

### Post by Headcase_Fargone on 2011-06-29
Hi all,

I'm running across an issue with permissions in a particular folder and was hoping to be pointed in the right direction.

My Ubuntu box is my media server, and I currently have a "TV" folder shared that I access from my HTPC.  I have Transmission set up to automatically download television episodes via RSS, then the SortTV script moves them from the download folder to an appropriately-named folder in the "TV" share and renames them to the correct episode number and name.

After all of this happens, software on the HTPC scans the media folder on a regular basis and downloads meta data for any new episodes it finds.  The problem is, when SortTV creates a folder (for a new season for instance) or even just moves a file over that file or folder is now locked and the HTPC cannot access it.  That is to say, it can read the files but cannot create new files like backdrop.jpg or episode descriptions.

Currently I have a "sudo chmod -R 777" command running every hour in Scheduled Tasks and am passing the sudo password in plain text in this command.  This seems like a horrible solution and just a bad idea in general, but it's all I've managed thus far.

Is there some way to set it so that any file or folder that is ever created in the "TV" share will be read/write accessible to anyone no matter who creates the file?

---

### Post by Ozymandias_117 on 2011-06-29
If HTPC runs as a specific user, you could add it to the group that SortTV uses for a slightly better solution. Not a great solution, but probably better than the current one.  :)

---

### Post by doas777 on 2011-06-29
ok, I have a recommendation (use SetGID) but first a few questions to make sure its right for you.

what user does SortTV run under, and what are the ownership/perms on teh files after they are created/moved by SortTV?
run ```
ls -al
``` within the directory to see, and post back some of the output.

are the users on both your HTPC and "server" using the same username and password? are they both members of the 'users' group?
to list the groups you are a member of run ```
groups <username>
```

so, what I would propose is that you use either SetGID or SetUID on the root TV share folder and all children. this will cause either the ownergroup or owneruser of newly created files to take on the ownership of their parent folder. 

on my home lan, most of my users are members of the Users group, so I setGID on my samba folders. that means that whomever puts content on the share, the ownergroup is always 'users' so all my accounts can access the contents of the share using group permissions rather than users. 

how does that sound?

---

### Post by Headcase_Fargone on 2011-06-29
Wow, quick responses.  The HTPC is actually running Windows 7 and since the SAMBA shares are set to allow anyone to access them I'm not entirely sure what it defaults to.

I'll turn off the chmod command on the scheduler and see what the permissions look like next time SortTV picks something up.

How do I determine what user SortTV is running as in Scheduled Tasks?

---

### Post by doas777 on 2011-06-29
> **Headcase_Fargone said:**
> Wow, quick responses.  The HTPC is actually running Windows 7 and since the SAMBA shares are set to allow anyone to access them I'm not entirely sure what it defaults to.

I'll turn off the chmod command on the scheduler and see what the permissions look like next time SortTV picks something up.

How do I determine what user SortTV is running as in Scheduled Tasks? so wait, the SortTV product is running on windows? if that is the case, the files should be created as being owned by the user being used to login to samba when connecting to the Downloads share. 

why don;t you give us abreviated 'ls -al' on all the key folders involved in this. that will prolly simplify matters.

---

### Post by Headcase_Fargone on 2011-06-29
> **doas777 said:**
> so wait, the SortTV product is running on windows? if that is the case, the files should be created as being owned by the user being used to login to samba when connecting to the Downloads share. 

why don;t you give us abreviated 'ls -al' on all the key folders involved in this. that will prolly simplify matters.

Nono, SortTV is a Linux script that I'm running on the Ubuntu box.  It's responsible for moving files from the download folder to the TV folder.

The only Windows software involved is a meta data grabber that scans the TV folder for television shows and downloads information on them (.txt and .jpg files) which it places in their respective folders on the Linux box.

Running ls -al it would appear the the folders being created by SortTV are owned by MY username.  Others are owned by nobody/nogroup.

---

### Post by doas777 on 2011-06-29
> **Headcase_Fargone said:**
> Nono, SortTV is a Linux script that I'm running on the Ubuntu box.  It's responsible for moving files from the download folder to the TV folder.

The only Windows software involved is a meta data grabber that scans the TV folder for television shows and downloads information on them (.txt and .jpg files) which it places in their respective folders on the Linux box.

Running ls -al it would appear the the folders being created by SortTV are owned by MY username.  Others are owned by nobody/nogroup.
sounds like a nice level of automation, cheers.

are the users on the differant boxes using the same username and password? if so, SetUID may be the best bet, whereas if not, using SetGID and making sure they are both in the same group would work fine. 

check out this wiki, (look specifically at "[FONT=Arial][SIZE=2]setuid and setgid on directories[/SIZE][/FONT]")
[https://secure.wikimedia.org/wikipedia/en/wiki/Setuid](https://secure.wikimedia.org/wikipedia/en/wiki/Setuid)

does that seem like it would suit you?
[B]
[/B]

---

### Post by Headcase_Fargone on 2011-06-29
> **doas777 said:**
> sounds like a nice level of automation, cheers.

are the users on the differant boxes using the same username and password? if so, SetUID may be the best bet, whereas if not, using SetGID and making sure they are both in the same group would work fine. 

check out this wiki, (look specifically at "[FONT=Arial][SIZE=2]setuid and setgid on directories[/SIZE][/FONT]")
[https://secure.wikimedia.org/wikipedia/en/wiki/Setuid](https://secure.wikimedia.org/wikipedia/en/wiki/Setuid)

does that seem like it would suit you?
[B]
[/B]

Is it safe to assume that the Windows box is accessing the SAMBA share as user "nobody?"  I never set up any credentials anywhere in Windows, and I'm not sure how that works by default under Linux.

---

### Post by doas777 on 2011-06-29
> **Headcase_Fargone said:**
> Is it safe to assume that the Windows box is accessing the SAMBA share as user "nobody?"  I never set up any credentials anywhere in Windows, and I'm not sure how that works by default under Linux.
it may be that that is the case. it depends on the share configuration. if you are using Security=user and you have the same username/passwd on each box, then you are probably authenticating without even noticing.

---

### Post by Headcase_Fargone on 2011-06-30
> **doas777 said:**
> it may be that that is the case. it depends on the share configuration. if you are using Security=user and you have the same username/passwd on each box, then you are probably authenticating without even noticing.

Windows box and Linux box usernames are definitely not remotely similar.  Neither would exist on the other box.

---

### Post by doas777 on 2011-06-30
then yes, if you are not being prompted or putting in a username/passwd on connect, then when you create files/folders  from a samba client, they would be created on the server under  nobody/nogroup (guest).
SetGID or SetUID should work, in this situation, to change the owner on write. 
that said however, since you have no authentication, everything relies on teh "Other permission", which seriously weakens the value of this approach. when you set the files to 777, only the last 7 is meaningful, at which point you might as well not have any user/group at all.

---

### Post by Headcase_Fargone on 2011-06-30
I think I'm on the right track now.  Thanks everyone!

---

