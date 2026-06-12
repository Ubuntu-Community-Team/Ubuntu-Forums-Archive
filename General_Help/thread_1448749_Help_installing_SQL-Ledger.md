---
title: "Help installing SQL-Ledger"
date: 2010-04-07
forum: General Help
---

### Post by 1968mb on 2010-04-07
Hello gang
I've been poking around for the last week trying to find a suitable small business accounting software that will work for us. To make a long story short I stumbled upon SQL-Ledger and it looks like a very good application just what we're looking for... and low and behold its in the repositories!
Anyway I installed the SQL-Ledger package but unfortunately there's no way to load or open this app. Synaptic shows its installed but there's no gui or and reference in the menu. Searching using the filter in the menu results in nothing. 
So I'm assuming SGL-Ledger just needs a gui associated with it to open it right?? 
Any help with this last step would be greatly appreciated... sure would make life allot easier on a number of people desperate to get away from QuickBooks

Thanks in advance

---

### Post by Oasu4g on 2010-05-12
I'm having similar issues.

@1968mb

#1. Make sure PostgreSQL is installed. You should be able to see it in your repositories. Personally, I'm having trouble getting it to start, but hopefully I will come across the solution to this soon.

#2. SQL-Ledger runs from your browser. Once you have PostgreSQL (the database server behind SQL-Ledger) up and running nicely, you will need to follow the instructions provided in SQL-Ledger's current [README]("http://www.sql-ledger.org/cgi-bin/nav.pl?page=source/readme.txt&title=README").

Make sure your computer meets the requirements, and follow the instructions for Installation with setup.pl. From my experience, the package in the repositories installs SQL-Ledger in /user/share/sql-ledger, so look for the files mentioned as being in /user/local/sql-ledger, there. I know it's confusing, but I think if we can work together we can get it working!

Best of luck! And also, I would appreciate any help from anyone else who has had success installing this program. This is a field I've never delved into before.

Regards,

Tim

**EDIT: I've found these links extremely helpful:

[s]http://ubuntuforums.org/showthread.php?t=1295043&highlight=sql-ledger[/s]
[http://ubuntuforums.org/showthread.php?t=1251151&highlight=sql-ledger](http://ubuntuforums.org/showthread.php?t=1251151&highlight=sql-ledger)

[s]The first one describes how to set the password for PostgreSQL[/s] ([color=red]not detailed enough[/color]), and the second is another topic for getting SQL-Ledger up and running. I will try these out tomorrow and try to remember to post my results.

**EDIT #2: I should post this here too:

[http://www.linuxjournal.com/article/7290?page=0,0](http://www.linuxjournal.com/article/7290?page=0,0)

Think of it as a primer on how SQL-Ledger is set up and works.

---

### Post by Oasu4g on 2010-05-22
Alright, so, I've gotten to the bottom of the error PostgreSQL reported at startup, which was causing the server to fail to start properly at boot.

I used this solution: [http://dancingpenguinsoflight.com/2010/03/dealing-with-could-not-create-shared-memory-segment-from-postgres-on-ubuntu/](http://dancingpenguinsoflight.com/2010/03/dealing-with-could-not-create-shared-memory-segment-from-postgres-on-ubuntu/)

Here is the topic I started for my problem: [http://ubuntuforums.org/showthread.php?t=1481533](http://ubuntuforums.org/showthread.php?t=1481533)

-------------------------------

Once I got PostgreSQL running at startup, I needed to give it a password. You can do this by entering the following command into the terminal:

```
sudo -u postgres psql postgres
```

Then give the PostgreSQL user, postgres, a password. Do this by typing:

```
\password postgres
```

Enter the password at the prompts, and make sure to save it. This is the password you will need to interface with the server.

Now we need to create a user in order for SQL-Ledger to interface with PostgreSQL. Do this by typing:

```
sudo -u postgres createuser -d -P sql-ledger
```

Enter a new password at the prompts (don't forget to save it); then enter "n" when asked both questions.

This *should* take care of PostgreSQL. I am downloading the newest version of SQL-Ledger as I type this, via the setup.pl file located in /usr/share/sql-ledger (see readme for more detail). I will post back if I am successful!

---

### Post by Oasu4g on 2010-05-22
I'm in!

Okay, so I navigated to /usr/share/sql-ledger and opened a terminal there; then ran:

```
sudo perl setup.pl
```

I chose Install and entered "www-data" for the owner and group, which is the owner and group for apache2 on my system.

Let it install, read the readme if you haven't already, and now, we need to make sure some permissions are set right for a couple of folders and files under /usr/share/sql-ledger, and change them if they're not set right (which I had to do).

I kept getting permission denied errors whenever I navigated to [http://localhost/sql-ledger/admin.pl](http://localhost/sql-ledger/admin.pl). I found this in the FAQ at: [http://www.sql-ledger.org/cgi-bin/nav.pl?page=misc/faq.html&title=FAQ](http://www.sql-ledger.org/cgi-bin/nav.pl?page=misc/faq.html&title=FAQ)

> Check if your webserver has write permission to write to the following files and directories:
   users/
   templates/
   users/members
 
   # chown nobody:nogroup users templates users/members

I just right-clicked on each file and changed the permissions through the Permissions tab.

And that should be it. I hope this helps some of you.


One more thing you might want to do is install phpPgAdmin:

```
sudo apt-get install phppgadmin
```

This will allow you more control over your PostgreSQL server through a graphical interface run from your browser, just like SQL-Ledger. Once you have it install, point your browser to [http://localhost/phppgadmin](http://localhost/phppgadmin) and then click PostgreSQL over on the side. You'll be asked for a username and password. Use the sql-ledger username and password you created earlier, and now you're able to manage the sql-ledger databases without muddling through the terminal!

Regards,

Tim

---

