---
title: "Nobody has greater privileges than me.  Nobody!"
date: 2011-11-18
forum: General Help
---

### Post by L a r r y on 2011-11-18
If I can't do it, nobody can.

Now with all humor aside, I have a permissions issue with my XAMPP server.

I have set up a path on my computer to duplicate the path found on my host's Webserver, a new branch from /home outside of my username's home folder.

I chowned it to belong to me, just as is my home.

I recently ran a Perl script that saves a file to the disk.  It did not have permissions enough with chmod 755 on the destination folder, with me able to write to the disk as owner.  Nobody is not a member of my group, so chmod 775 did not give enough permissions, and after it did write on chmod 777, the owner is nobody and a member of nogroup.

Now I suspect that I can write to the file if I log in as root, or sudo, either that or chown it to something I can write to, or chmod it to 777.

In my web server environment, owner is 940 and the group is 940, actually a different set of numbers, but both are the same number.

Now, whereas my script belongs to me and the script's file belongs to nobody on my computer, they both belong to 940 on the server on the Internet.

Should I set up a different user and have the server run as that user, instead of as nobody, and I log in to that account as well, thus allowing a folder chmod of 755 give us both permission to write to what is currently nobody's file, or should I add nobody to my group and use a chmod 775 so both nobody and I can write to the file?

When setting up the XAMPP, I didn't fully understand the permissions setup, though I knew nobody was involved with it.

I've written this post hopefully to receive the requested help, but also I hope nobody goes away without a smile!  :lolflag:

---

### Post by L a r r y on 2011-12-04
> **L a r r y said:**
> If I can't do it, nobody can.

*OK, I was being a wise acre and playing with the user "nobody" in making a humorous approach to a serious question.:lolflag:  I got 137 views in 2 weeks, but no help*.

**Thank you** to everyone who took the time to read, and I hope you did get a chuckle.  This time around though, I will refer to the user "nobody" as _user:nobody_, and similarly "nobody's" group as _group:nogroup_.  Or place quotes:  "nobody" and "nogroup"

So here again is my question:

**I installed XAMPP** on my Ubuntu computer, with /opt/lampp/htdocs as its Web root folder.  > /opt/lampp/htdocs/index.html would open as > [http://localhost/index.html](http://localhost/index.html).

My logon name is "myself" and so I have /home/myself as my home folder.  I am user:myself.

I copied my online Web site files from the host server onto my computer in **/home/account/public_html**, and made that home folder owned by user:myself, as a member of group:myself, just as is myself's home.

I edited the config file for the server to use **/home/account/public_html** as the server root for my opening index.html.

In XAMPP, scripts run as user:nobody a member of group:nogroup.

Trouble is, I am not a member of "nogroup" and I have not the privileges of user:nobody to edit or remove the file, **unless I do a sudo** and **if user:myself creates the file, the script with the privileges of "nobody" cannot overwrite it**.  (I didn't try to sudo create the file and see if "nobody" can overwrite a "root" creation.)

Only chmod 666, where the world has privileges to read and write to the existing file created by "myself," can "nobody" write to it.

Root must be a read-write member of "nogroup" for I can sudo overwrite or remove "nobody's" file.

I had to sudo everything in htdocs upon completion of installation.

If I did set up a new user-group combination, I would then need file permissions for my ftp client to save in this Web folder the content I download from my site.  I have no problem there with the current setup.

Any suggestions?

Should I set up a new group and have both "myself" and "nobody" a member, and chmod 660 to give both the script and myself access to the file for read and write, or make user:root a member of the group and chmod 660 so both "nobody" and "root" have equal access?

**This server is for local development, not a publicly hosted site, by the way.**

---

