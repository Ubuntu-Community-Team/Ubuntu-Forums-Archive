---
title: "Which is better: at, anacron, or fcron/fcronq"
date: 2012-09-13
forum: General Help
---

### Post by Ralph L on 2012-09-13
I want to periodically schedule my backups.  However, if my computer is down, I want any backups that were scheduled for the down period to run shortly after the computer comes back up.  I am somewhat confused over what application to use for this purpose.  I know cron won't run missed tasks after the computer restarts.  Other applications that will work seem to be at, anacron, and fcron/fcronq.  Which is best????

I have used fcron/fcronq is the past and had problems getting it installed (I don't know why).  Also fcronq (the gui front end) was pretty basic and had a (minor) bug.  I have found anacron discussions on the web, but have never used it.  I also see something called "at".  I couldn't find much info on it.

Can anybody tell me what direction I should go and why?  What is the most popular way of getting this capability?  Are there gui front ends for any of them other than fcron, which has fcronq?  Have any of them been depreciated, and headed for non use?  Is there a direction that ubuntu is headed?  Do they all have adequate features?

Thanks in advance,
Ralph

---

### Post by kjohri on 2012-09-14
Use anacron. The following link gives more information,

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

### Post by Ralph L on 2012-10-14
I didn't have good luck with anacron.  See [http://ubuntuforums.org/showthread.php?t=2058422](http://ubuntuforums.org/showthread.php?t=2058422).  Although I finally got it to mostly work, I could never get the sendmail results from my executing script to Thunderbird email.  Because anacron always runs under root, it always sent its sendmail (email) to root's mailbox, rather than to my mailbox.  

I decided to go back to fcron/fcronq and had much better luck, although there is a bug in fcronq that I had to work around (more on that later).

Fcron seems to run as a task under the user that created it, and sends mail to that user's (in my case Thunderbird) sendmail mailbox.  Also, fcron sets up an fcrontab file for each user so in a multi-user system, nobody needs to have root access to use it. And fcron will schedule down to the minute making script schedule testing much easier.   In addition, I like GUIs and there is no GUI to front end anacron.

Since fcron/fcronq are not in the ubuntu repositories I had to go directly to their respective web sites to get them.  fcron is at [http://fcron.free.fr/doc.php](http://fcron.free.fr/doc.php).  On the left side is a menu that includes both Docs and Downloads.  I downloaded fcron-3.0.6 for the USA.  After uncompressing the tar file, I found the install instructions at ./doc/en/txt/install.txt.  Although it is not included in the install instructions, it is necessary to first create a userid and groupid for fcron.  I did this by:
```
sudo groupadd -g 200 fcron && useradd -d /dev/null -c "Fcron User" -g fcron -s /bin/false -u 200 fcron
```

I then used synaptic to install sendmail (search for sendmail in synaptic).  It is also necessary to set up a sendmail mailbox in Thunderbird or other email program.  In TB go to Edit>Account settings, and at the bottom of the left column, select Account Actions>Add Other Account, and select Unix Mailspool (Movemail). I set email address to my user name (ralph), my Reply-to-address to ralph, my server name to ralph-laptop (my computer's name), my User Name to ralph, Outgoing Server port to 25, no authentication.

I then installed fcron using the commands:
```
cd directory_in_which_I_ungzipped_fcron
./configure
make
sudo make install
```
I hit the enter key to use the default answer for all questions.

Next I installed fcronq, the rather primitive GUI for fcron.  I downloaded FcronQ-0.4.7.tar.bz2 from [http://code.google.com/p/fcronq/](http://code.google.com/p/fcronq/).  It needs QT4 using Python 3.

Using Synaptic I installed python3-pyqt4.  It also installed python3, python3-minimal, python3-pyqt4, python3-sip,python3.2, python3.2-minimal. 

Using Synaptic I installed pyqt4-dev-tools.

Then I did the "make" and "make install".  "./configure" wasn't necessary.

```
cd directory_in_which_I_ungzipped_fcronq
make
sudo make install

```
I created a launcher for FcronQ by going to Main menu>Preferences>Main Menu, clicking the New Item button on the top right, naming it FcronQ and entering "FcronQ.pyw" in the Command box.  I clicked it and it brought up an empty fcrontab table. However, the column headings were missing from the first 4 columns.  These should have read Check to Run, Environment, Options, Schedule time/date, Command.  Right click in the table area and select "Append" to add a row to the table and schedule a task.  Double click in the column and row to add data.  FcronQ has no documentation, but follows the fcrontab documentation ([http://fcron.free.fr/doc/en/fcrontab.5.html](http://fcron.free.fr/doc/en/fcrontab.5.html)). 

The five columns in FcronQ for my daily backup were:

Checkbox checked; Environment blank; &bootrun(true); 00 14 * * *; export DISPLAY=:0.0 && /usr/local/bin/lbprofile1 

Note that "export DISPLAY=0.0" is required if you want to display something on the screen, perhaps using zenity.  Also, note the full pathname to my script.  For some reason fcron required this.  This statement (row) runs the script lbprofile1 at 2:00 pm every day and uses zenity to display a message on the screen.

---

