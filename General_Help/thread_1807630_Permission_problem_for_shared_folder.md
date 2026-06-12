---
title: "Permission problem for shared folder"
date: 2011-07-19
forum: General Help
---

### Post by Amitabha on 2011-07-19
[COLOR=#000000][FONT=Arial]Hey, guys. [/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]I recently installed Ubuntu Server (11.04) on my old computer just for testing purposes, therefore I kindly ask those of you who chooses to reply to give as clear and concise answers as possible, as I am not very familiar with all the Linux lingo and commands. I’ve already tried searching this forum for answers, aswell as google. [/FONT][/COLOR]
 
 

[COLOR=#000000][FONT=Arial]Explanation of what I want my system to do:[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]I want to use SABnzbd to download files to a specified folder hierarchy (usenet<movies, music, books etc.) where usenet is the parent folder.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I also want to share these folders to my family on our LAN by using Samba.[/FONT][/COLOR]
[/LIST][COLOR=#000000][FONT=Arial]I have stumbled upon a problem when it comes to file and folder permission.[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]SBNzbd runs under my user(*****) which is part of a group called downloads. I want my user to have all permissions (rwx), the group should have read and execute (they need execute permissions to browse a folder with read-only permissions, am I right?) and others should have no rights to these folders. [/FONT][/COLOR]
 
[FONT=Arial]I have installed both Samba and SABnzbd and I think that everything was installed the right way.[/FONT]
 
[FONT=Arial]This is how I shared folders in smb.conf:[/FONT]
```
[Anime]
comment = tv on *****
path = /home/****/Downloads/USENET/Anime
guest ok = no
browseable = yes
read only = yes
create mask = 0000
directory mask = 0000

```
 
[COLOR=#000000][FONT=Arial]These are the commands I have run to try to give the right permissions for the parent folder plus the subdirectories:[/FONT][/COLOR]
```
 
sudo chmod -R u+rwx, g+rxs, o-rwx /path/to/parent/folder
sudo chown -R myusername:downloads /path/to/parent/folder

```
 
[COLOR=#000000][FONT=Arial]I wanted to make sure that everything was working well, and at first I thought it did. I was able to browse the directories and also watch movies and stream music. The problem occured instantly after I made SABnzbd download a new file. The file was downloaded, extracted and put into the right directory (used SABnzbd's category function). When everything seemed to be perfectly fine I tried to browse (by using a user I made for my family to use. It's part of the group called download) the newly created folder which contained the downloaded files, and it gave me an error message that told me that "I do not have the correct permission to do this". [/FONT][/COLOR]
[FONT=Arial][/FONT] 
[FONT=Arial]What I did next was to check if the user and group was correctly set to the new files, and they were. Therefore I now suspect SABnzbd to create files with the wrong permissions by default. My umask is set to 022.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Are anyone of you able to guide me in the correct direction? Are[/FONT][FONT=Arial] there any other information that I should provide to make it easier to help?[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks in advance,[/FONT]
[FONT=Arial]Amitabha[/FONT]

---

