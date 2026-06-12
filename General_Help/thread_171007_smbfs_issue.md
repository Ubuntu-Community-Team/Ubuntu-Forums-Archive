---
title: "smbfs issue"
date: 2006-05-05
forum: General Help
---

### Post by kupajava on 2006-05-05
When trying to mount a win2k3 share on my ubuntu box, both manually and in the fstab file, I have a really odd problem.  I am able to open shares mounted the very same way on other desktop machines on this network running other linux distros but when I try it in ubuntu the folder that I mount the share to shows up as a file and cannot be opened or modified.  here is my fstab file (locations modified to protect ip):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//(ip of server)/music        /mnt/music  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

the credentials file contains my username and password. 

I have been banging my head against a wall with this for more than a week.  I have seen many sites that describe the process of mounting shares in ubuntu and with some slight differences all describe the process the same way.  Samba is installed on this machine and the network settings are correct. I have been able to get the shares to mount by changing "smbfs" with "cifs" but mounting that way forces me enter my account pw for each share I mount during the startup, which is really annoying. 

Is anyone else having a similar problem?
Is anyone else able to mount a win2k3 share this way and not having any problem?
Does anyone know how to fix this?

I would love to hear from anyone about this, this problem is driving me crazy.

---

### Post by ScreemingBlue on 2006-05-05
I'm sure you have checked this already but has the root account got read access to the .smbcredentials file?  Also make sure the windows firewall is'nt blocking anything.

---

### Post by kzutter on 2006-05-05
Make sure /mnt/music is indeed a directory and not a special file.
Check what the permissions are on /mnt/music *before* the share is mounted. They should  be set to what access you want the user(s) to have after the share is mounted.
You probably want 777 as told by your fstab entry.

p.s. You may need to add rw to your fstab entry - I am not at my linux box right now or I would share my fstab that works great

Here it is:
//myth/Ken /mnt/mars/Ken smbfs rw,credentials=/etc/samba/credentials,uid=ken,gid=users,fmask=777  0 0

---

### Post by Jose Catre-Vandis on 2006-05-06
um, what filesytem is your w2k3 share?

if it is vfat then you will be able to read/write, if ntfs then only read.

Also the username and password credentials you have in file need to be a samba user /user on the w2k3 box

---

### Post by kupajava on 2006-05-06
Thanks for the many responses.  I have now checked and tried them all.  Ill go through them one at a time:

1. root has access to smb file:  went ahead and made sure of this after reading the post, credential file definately does has access for root.  The file is owned by root and root has full access.

2.Make sure /mnt/music is indeed a directory and not a special file (also permissions):   Did this.  Went through and made sure that each directory had 777 access when I created them, double checked each when I read this response  to make sure by remarking out the lines in fstab and restarting, then chmoding the folders to 777. Good call tho...  Remember, when I change the term smbfs in the fstab to cifs, I am able to mount, although it is supposedly not a good way to connect and has instability problems that dont come with smbfs, also, I want to figure this out for the future and fix it not just change it to cifs, but to answer the question...  yes they are folders, and they all have 777 access.

3. You may need to add rw to your fstab entry:  This is what I was hoping to get from this post, I wanted to compare my fstab to a known working one...  I changed my fstab to compare with kzutter and still the same issue.  here is the line (there are 5 but they are all more or less the same except the share and mount name) 

//(server ip)/music /mnt/music  smbfs rw,credentials=/root/.smbcredentials,uid=(user),gid=users,fmask=777   0       0

(address and username modified to statement in parenthesis)

4. What filesytem is your w2k3 share:  Working with ntfs here, however, again when I change the "smbfs" to "cifs" i get r/w access (although it makes me input my linux user pw at mount for each share on system startup... weird, huh?) so I know that this shouldnt be a filesystem issue in that manner.  However, at this point I wouldnt mind having read-only if I could get the mounts to show up as folders with the line as it is above (smbfs not cifs) so I knew that this issue was fixed.

5. Samba user credentials in credentials file have to be samba user /user on the w2k3 box:  The user in the credentials file is a user on the w2k3 box with administrative rights.  Unless there is something special necessary to make this users info samba specific in w2k3 then Im not sure they could have higher permissions then already there.

Again, thank you for all of your responses, I think that together we can resolve this if we keep at it.

I am begining to think that there might be something unusual going on here that is maybe not ubuntu specific but might be deeper on this system

Any other ideas or comments?

---

### Post by Jose Catre-Vandis on 2006-05-06
OK I have just tried this out on my two boxes, and got the share to work. I'll explain what I did with what I have.

A dual boot box with XP and ubuntu. The XP partition MUSIC, is mounted as a drive on Ubuntu (e.g. you get a drive icon on the desktop). lets call this XP-U

An ubuntu box on the same lan. lets call this SERVER

Firstly, samba is installed on both machines

On XP-U
I used the GUI Share Folders to share MUSIC
I then checked smb.conf which gave the following:

[MUSIC]
path = /MUSIC
available = yes
browseable = yes
public = yes
writable = yes

A samba user called bill with password ben
bill is also in the smbuser file as bill="network_username"

Now on SERVER

Opened up a terminal and typed

sudo mkdir /media/XPMUSIC

sudo mount //10.10.10.60/MUSIC /media/XPMUSIC -o username=bill,password=ben,dmask=777,fmask=777

Hey presto, a drive icon called XPMUSIC appeared on the desktop and I was able to browse the folder. Haven't put the effort in yet to check permissions, but this is good enough for read only. Hope this helps, and doens't drive you to further despair because I can and you can't! Now I know that i am running this through Ubuntu so really this is a LINUX to LINUX share, i will have to reboot into Windows and try again that way. I would try manually mounting first, its easier to play with the parameters and you know it will share, fstab can follow later

Other thoughts, you are happy with the share permissions on the W2K3 box, can't be simple file sharing so worth just checking this through again, although you did say you could get at the files from other boxes?

---

### Post by kupajava on 2006-05-06
Thanks for the response, Jose Catre-Vandis, I tried to replicate this example you posted and here's what happened for me (sorry about another really long post here):

1. I went into the fstab and put # in front of the lines that mount the network shares and rebooted the machine so that Im starting with a clean slate.

2. After reboot, I went into the mnt directory where the mount folders are and saw that the folders now looked like folders again, show up as folders and can be opened, they can.  Checked permissions for "music" folder in /mnt, the permissions are set to 777 r/w/e for everybody. Closed the nautilus screen.

3.  Opened a terminal and typed: (ip, username and pw replaced)
 
sudo mount //(server ip)/music /mnt/music -o username=(xpusername),password=(xppassword),dmask=777,fmask=777

as always, the term then asks me for my pw to operate as sudo and I give it, the line goes through without any errors.

4: I navigate nautilus over to /mnt and, as before, the folder /music now appears as an unknown file instead of a folder.  when I check the permissions it says that "the permissions of "music" cannot be determined"  which is what is happening when my fstab mounts these folders.

So this definately recreated the situation.  As for the w2k3 side, the user that Im using to open the share has full permissions on this folder (somewhat loose as win permissions go, but I wanted to test with a powerful account so that I could boil down from there when it works) and is able to be opened from other clients running xp. 

I rebooted and this time typed in "sudo mount -t cifs //(server ip)/music /mnt/music -o username=(xpusername),password=(xppassword),dmask=777,fmask=777" 
and after two messages stating not to use dmask and fmask with cifs I check the mnt folder and the share is now mounted with 777 access.  I created a test file and I am able to read and write to the mount with no problem.

The big question here, something that I missed up until now...  Do I need to install samba on the W2k3 Server box?  I hadnt read that I would have to up until now, but I could see why I should if it is suggested.  And, what is the difference between using smbfs and cifs, why is only cifs working for me on this client?

It seems that this problem so far is only able to be replicated on this one client.  Should I try re-installing samba?  I have followed more than one step by step how-to with the same issue, so Im wondering if I somehow have a deeper problem with my Ubuntu install that needs to be resolved and is specific to this particular client.  Unfortunately, I dont have a spare client that I could install Ubuntu to and isolate the problem to being on this machine.  Anyone have any idea of any possible install issues that could break samba installations or possibly  mess up the part of the OS that handles smbfs on the Ubuntu side?  Im grabbing at straws here but this has to be resolvable if others cannot replicate the problem.

---

### Post by kzutter on 2006-05-06
Hmmm... this seems to be gettin out of hand.

1. It makes no difference what the file system is on the Win box.
2. My fstab refers to a group (users) that may not be present on your Ubuntu
3. You cannot install samba on windows - the SMB(CIFS) protocol is standard on windows
4. I have never used samba with a Win2003 box - I was assuming it would act the same as WinXP, but I amy be wrong. Google this to see if anything comes up.
5. Do you have the smbfs package installed on the Ubuntu box?? I assumed you did. Re-installing Samba may or may not help - but do check for latest version / broken packages, etc.
6. I see you use the mount command and not smbmount. smbmount is provided by smbfs. We may be onto something here. Anyway smbmount should give you better error message.

Crossing my fingers!

---

### Post by Jose Catre-Vandis on 2006-05-06
[QUOTE=kupajava]Thanks for the response, Jose Catre-Vandis, I tried to replicate this example you posted and here's what happened for me (sorry about another really long post here):

1. I went into the fstab and put # in front of the lines that mount the network shares and rebooted the machine so that Im starting with a clean slate.

2. After reboot, I went into the mnt directory where the mount folders are and saw that the folders now looked like folders again, show up as folders and can be opened, they can.  Checked permissions for "music" folder in /mnt, the permissions are set to 777 r/w/e for everybody. Closed the nautilus screen.

3.  Opened a terminal and typed: (ip, username and pw replaced)
 
sudo mount //(server ip)/music /mnt/music -o username=(xpusername),password=(xppassword),dmask=777,fmask=777

as always, the term then asks me for my pw to operate as sudo and I give it, the line goes through without any errors.

4: I navigate nautilus over to /mnt and, as before, the folder /music now appears as an unknown file instead of a folder.  when I check the permissions it says that "the permissions of "music" cannot be determined"  which is what is happening when my fstab mounts these folders.[/QUOTE]

From this it seems you are getting a share? Yes? Can you see the files in nautilus, can you copy them to your Ubuntu box?. As your W2K3 box is ntfs, it is not recommended to "write" in any case. Have we been chasing our tails here?

---

### Post by kupajava on 2006-05-06
Kzutter:

1. noted
2. users is there and the linux account I am using is a member
3. also noted
4. Found some info on encryption settings in w2k3 that unfortunately, didnt help.
5. I just upgraded to dapper, so as far as I can tell, yes
6. I will have to reboot to try 6, I will let you know after a reboot if I get new info.
edit: after a reboot, checked using previous mount line with smbmount instead of mount, still get folder turning into unknown file that cant be opened at all instead of share that can be opened like when I use cifs (this file is the actual mount folder, mind you, not any files ON the share, its the actual share that cant be opened and when right clicked becomes "unknown file")

Jose Catre-Vandis:

I am not able to open the mount as a share after either a manual or fixed mount using smbfs, I am able to open it if I am using cifs.  This is the problem and its incredibly confusing.  I really don't even care about write access, just read, and even tho it works with cifs I have heard that this is not a good way of connecting to windows shares and can cause serious problems.  This is why I am trying to figure out a way to connect using smbfs instead of cifs and also figure out what is wrong with my setup that is complicating this that is not wrong with most setups.  Not so much chasing the tail but maybe not completely necessary if cifs is stable and what I heard about cifs is incorrect or outdated.  So, I hope you can see how frustrating this is.

---

### Post by kzutter on 2006-05-06
I was just looking at the man page for mount.cifs.
You know, CIFS is a successor to SMBFS, I believe that SMBFS is no longer maintianed by the Samaba crew.
Since it (CIFS) works for you, perhaps you are barking up the wrong tree.
I see it has the same mount options as smb, so you can still use a credentials file.
You should not have to give it your password,etc all the time.

p.s. I didn't know you are using dapper beta - you are posting to the breezy list

---

### Post by kupajava on 2006-05-06
kzutter:

Thanks for all your help bro,  I think we got this thing all figured out now-

1- I just today upgraded to dapper from breezy since my second to last response on here about 2 or 2.5 hours ago.

2- Even tho I still had the smbfs prob after the upgrade, I just went back and changed them all to cifs and now its working great, no longer unstable as far as I can tell, and (since the upgrade) no longer asks for all of the passwords, etc

IN CONCLUSION:

If anyone is having problems mounting Windows Server 2003 shares in Ubuntu Dapper, you should use "cifs" instead of "smbfs" in your fstab or mount.

example is:

//(server ip)/music /mnt/music cifs rw,credentials=/root/.smbcredentials,uid=(user),gid=users,fmask=777 0 0

where (server ip) is your server ip, .smbcredentials contains your win username and pw, and (user) is your linux username.  

as far as I can tell, the Issue is Resolved! :p

---

