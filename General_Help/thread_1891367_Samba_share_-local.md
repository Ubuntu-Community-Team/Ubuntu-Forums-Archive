---
title: "Samba share -local"
date: 2011-12-05
forum: General Help
---

### Post by Quarkrad on 2011-12-05
My wife and I have 10.10 machines about 3ft apart - we usually exchange files via a stick but I thought I would set up sharing for those times both machines are on.  I have, via nautilus, enabled Sharing on two folders on her machine. On my machine via Places, Networking, Windows Network, Workgroup I can see two icons (my wifes machine and mine).  If I double click on my wifes machine icon I can see the two folders I share with her.  The problem is I can copy to the two shared top level folders but not sub folders within them - permission denied.  The sharing folders on my wifes pc sit in a NTFS partition.  As a newbie I did not set up any permissions as such  - just ticked all three boxes/options in the Sharing Option Window when I initially set it all up.  I'm almost there - just need to extend permissions to the sub folders. (Currently she is the owner of all the folders - not sure how/where/how I include myself.  Am I seen as a guest?).

---

### Post by Morbius1 on 2011-12-05
I read through your post a couple of times and something just doesn't make sense to me. It all comes down to how the ntfs partition is being mounted on your wife's PC. If you didn't add anything to fstab and you mount it through Nautilus then the ntfs should have ownership = wife with access limited only to "wife". That would be for all folders and files within that partititon. But then you wrote this:
> The problem is I can copy to the two shared top level folders but not sub folders within them - permission denied. That doesn't happen with ntfs. You can control permissions between folders and files but not between folders and subfolders so I really don't know what's going on there.

** Quick answer:**
On your wife's machine:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - I'd put it right under the "workgroup" line:
```
force user = your-wifes-login-user-name
```Save the file and restart samba:
```
sudo service smbd restart
```Wait a few minutes and then see if you have access to the share.

You are indeed coming across as "guest". "force user" will convert "guest" to whatever your wife's user name is. If she has access to all the subfolders locally on her machine so will you.

---

### Post by Quarkrad on 2011-12-05
You have helped me before and again this time - thank you and sorry for not explaining enough.  On my wifes pc she has her normal 'home' folder on her ext4 partition within the ubuntu 10.10 install.  Additionally she has a ntfs partition where she stores historic data files - legacy from our winxp days.  There are many spreadsheets that are inter linked on the NTFS partition so it was easier to leave it 'as is' and access it from the ubuntu side via Libra Office.  I installed the *NTFS Configuration Tool* via the Software Center when I set her machine up and it is automatically mounted on boot.  Your addition to the .conf file did the trick - I have successfully transferred a large number of photos from my machine to hers.  Should we wish to do the reverse I assume I just reverse the process on my machine. Thank you again.

---

