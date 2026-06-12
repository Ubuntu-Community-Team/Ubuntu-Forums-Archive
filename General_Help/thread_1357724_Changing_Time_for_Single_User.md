---
title: "Changing Time for Single User"
date: 2009-12-17
forum: General Help
---

### Post by hwttdz on 2009-12-17
I work on a system which is unfortunately 12 minutes (at the moment) offset from real time.  I am not admin on this system.  I wonder if there is a way that I can offset the date that I see by a certain amount of time.  Said another way is there a way I can set the time for my user without changing the time for all users (which I don't have permissions to do).  Perhaps a timezone offset of 12 minutes and however many seconds?

---

### Post by DeMus on 2009-12-17
> **hwttdz said:**
> I work on a system which is unfortunately 12 minutes (at the moment) offset from real time.  I am not admin on this system.  I wonder if there is a way that I can offset the date that I see by a certain amount of time.  Said another way is there a way I can set the time for my user without changing the time for all users (which I don't have permissions to do).  Perhaps a timezone offset of 12 minutes and however many seconds?

Restart your computer and enter the BIOS
Change time there to match your local time
Save settings and quit, so the computer will reboot normally again.

---

### Post by hwttdz on 2009-12-17
I'm sorry, perhaps I was not clear, I am not a system admin, meaning changing bios is out of the question.  As are any sudo commands, as are anything that would require physical access to the machine.  I have ssh access with x forwarding, and I can change files in my ~ directory.

---

### Post by pricetech on 2009-12-17
You should report the discrepancy in the system time to the administrator of the computer so it can be corrected.

---

### Post by hwttdz on 2009-12-17
Great idea in theory, and "in theory, there's no difference between theory and practice...".  

I have my reasons for not wanting to bother our admin, including he always has bigger fish to fry, like making sure the cluster works, and because I need to save my beans for those "so I had a file in my home directory last tuesday named make_templates.pl, do you think I could get a copy of that" instances.  That said I might shoot him a note anyways.

---

### Post by MartyBuntu on 2009-12-17
> **hwttdz said:**
> 
I have my reasons for not wanting to bother our admin, including he always has bigger fish to fry...

Seeing how incorrect time settings can play ABSOLUTE HAVOC with mail servers, etc...I'd say that's some pretty big fish.

---

### Post by hwttdz on 2009-12-17
Good thing this machine doesn't run a mail server...  Sometimes I feel like my virtual image just radiates incompetence.

---

### Post by hwttdz on 2009-12-17
Getting back to the original question 

wget 'ftp://elsie.nci.nih.gov/pub/tzdata*.tar.gz'
tar -xf tzdata2009s.tar.gz
gedit (or other the offending file, in this case northamerica)
my changes:
# Zone	NAME		GMTOFF	RULES	FORMAT	[UNTIL]
Zone America/New_York	-4:56:02 -	LMT	1883 Nov 18 12:03:58
			-5:12	US	E%sT	1920
			-5:12	NYC	E%sT	1942
			-5:12	US	E%sT	1946
			-5:12	NYC	E%sT	1967
			-5:12	US	E%sT
(where I probably only needed to change the last two lines to read -5:12, possibly only the last one, not quite sure).

zic -v -d ~/time_zone northamerica (compile the time zone files, I'm not even sure this is proper syntax (zic isn't terribly well documented and I didn't look through the source) but significantly it did work)

Then in .bashrc
export TZ="/path/to/users/home/time_zone/New_York" (or whatever other time zone file, this specifies which time zone file to use)

For those end of the world theorists I did let sysadmin know.  

Answering my own original question yes it is possible to change the timezone for a single user by setting the TZ variable to point to the time zone you want, it is also possible to make a custom timezone file using the directions I outlined above.

Finally yes there are still issues with this solution, like if I edit a file from this machine then switch to another and ask what time the file was modified it will be off (as it was before), so really I've only fixed the "date" command and in my case the prompt (which tells me the time of day).  But in my case the time of the prompt being off was a bit annoying (and now it's not).

---

### Post by dcstar on 2009-12-17
> **hwttdz said:**
> 
.........
Finally yes there are still issues with this solution, like if I edit a file from this machine then switch to another and ask what time the file was modified it will be off (as it was before), so really I've only fixed the "date" command and in my case the prompt (which tells me the time of day).  But in my case the time of the prompt being off was a bit annoying (and now it's not).

All internal timestamps use Universal Time, not local time, so whatever your set your local shell time to will not affect this internal timestamp - and if the base system does not have this correct then they will also not be correct.

---

