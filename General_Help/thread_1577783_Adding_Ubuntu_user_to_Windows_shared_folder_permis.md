---
title: "Adding Ubuntu user to Windows shared folder permissions"
date: 2010-09-19
forum: General Help
---

### Post by pspkicks316 on 2010-09-19
I have a shared folder on my Windows computer on my network. I'm able to mount the shared folder in Ubuntu on my laptop with no problems whatsoever, but only root has write access. I need my normal user to have write access as well so I'm not constantly going to Terminal just to copy something over. 

The main reason I have this setup is so that I can develop using my laptop and desktop without needing to store a local copy on my laptop and then sync it back over.

I tried setting permissions to full for everyone on the share in Windows but had no luck. I can only set permissions for local system users and not anyone on the network. I set up samba in Ubuntu so that Windows sees and can access my laptop as well. That didn't help me either.

Is there any way that I can do this? Is it a samba problem? Windows? Ubuntu? Any info will be helpful.

tl;dr : I have a Windows share and can't set permissions to let my Ubuntu user write to it. Help?

---

### Post by robsoles on 2010-09-20
Welcome to UF, I hope I am not too harsh, sorry for the wait, there are plenty better than me we can attract to your thread if it comes to that :D

Please tell us which version of Windows?

How are you mounting the share from the Windows PC? If by /etc/fstab  then please post yours (killout passwords present in your /etc/fstab  file with x's or #'s, we don't need them ;)) so we have a little more to work with.

Does your Windows user have a password? Are you using 'simplified file  sharing' in Windows? (If in XP then open 'my computer' and goto  'tools'->'folder options', bottom or near bottom of list under  'view', is "Use simple file sharing" checked?)

Sorry my only help so far is questions, I'm sort of betting that you have an interesting fstab entry or no password on your user in Windows or something, but anybody needs to know more to help you and your thread is getting a bit old!

[COLOR=Blue]Actually[/COLOR], (WINDOWS) maybe it's as simple as telling you to make a user on your Windows PC and give them a password, kill the share (close it and unmount it) and remake the share and give only this user permission to read/write the share.

(UBUNTU) Delete that line in your /etc/fstab file if you've made one to mount this for you. Open 'Network' under 'Places' and see if you can't find the computer in the 'Windows Network' I hope you see in 'Network'. If you don't find it you can press [CTRL]+[L] to make the location editable and enter 'smb://your-Windows-PC-friendly-name/', if it doesn't come up then get the IP address of the Windows PC and retry with 'smb://w.x.y.z/' exchanging the IP address for w.x.y.z!

At some point of opening the connection to the Windows PC you should be challenged for the password and it may be presented as 'username, domain, password' - if it doesn't let you open the share then try the Windows PC's ''friendly name'' as the domain name.

Try writing to the share. If you can write then add it to bookmarks.

---

