---
title: "Apache not showing new directories"
date: 2009-08-29
forum: General Help
---

### Post by Kewley on 2009-08-29
Edit: I found the problem. I tried to create a link to the www directory, but some how copied the directory to the desktop...stupid I know :P.

I'm running a system that used to be solely a server enviroment, but which I installed a desktop on top of after my main laptop broke. 

My problem is that apache will not show files/changes to files/new directories created by using the "Left-Click->Create Folder" method. Instead I must open a terminal and use the "mkdir" command (under the same user). 

Im certain this use to work perfectly fine, and I can see the files I create if in the file system window. But not if they are created via the terminal.

I've tried restarting the apache service/whole system, and chmod-ing the web directory (chmod -R 0777 /var/www) to no avail. All pacakges are fully up to date (running 9.04).

Any help would be greatly appreciated :).

---

