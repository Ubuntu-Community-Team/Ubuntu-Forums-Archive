---
title: "Web GUI to send BASH Commands?"
date: 2011-09-06
forum: General Help
---

### Post by U2XS on 2011-09-06
I have an Ubuntu server and I'm playing around a bit to learn a little more.

I'd like to set it up so that if I press a button, the server receives the command to restart Apache.  Or maybe even allow a textbox with a submit button to type whatever I want.

I do realize the kind of security risk that this poses.  It is only going to be for private use, not publicly announced and password protected.  Can anyone tell me the best way to make this work in Ubuntu?  I was thinking PHP can update a file on the web side & Ubuntu can run a cron once per minute to read it.  Is there a better way?

---

### Post by CharlesA on 2011-09-06
You can use webmin to manage a server from a browser, but I am not sure of any way to send commands directly to the host thru the browser outside of that.

Why not just ssh in and run the commands?

---

### Post by aeiah on 2011-09-06
there's [http://phpshell.sourceforge.net/](http://phpshell.sourceforge.net/)

but as the above poster says, why not just ssh?

---

### Post by MrWestwood on 2011-09-06
Another one for Webmin

---

### Post by U2XS on 2011-09-06
Thanks guys.  I'll look into PHPShell & webAdmin.  They both look like tools I'd like to learn about.

I use Zoneminder (surveillance system) on Ubuntu and it has a memory leak.  I wanted to create a button that just sends the command to restart Apache services.  I don't want to teach everyone who uses the camera's about SSH or BASH commands.

As a game, I'd like to expand on it and learn similar commands.

---

### Post by CharlesA on 2011-09-06
You'd need root access to restart apache, even if it's password protected - being able to access it from a browser could cause problems - XSS comes to mind, even if it's not targeting your specifically.

Why not just set up a cronjob to restart apache at a specific time?

---

### Post by aeiah on 2011-09-06
> **CharlesA said:**
> 
Why not just set up a cronjob to restart apache at a specific time?

or better still (if you cant get zoneminder to stop leaking), why not run a cronjob every 5 minutes that monitors your system's memory, and when it gets really high it restarts zoneminder/apache?

---

### Post by CharlesA on 2011-09-06
> **aeiah said:**
> or better still (if you cant get zoneminder to stop leaking), why not run a cronjob every 5 minutes that monitors your system's memory, and when it gets really high it restarts zoneminder/apache?

+1 to that. I'd probably do that if I had the problem. It's probably a more complicated script to write, but it would be worth it in the end.

---

### Post by U2XS on 2011-09-06
> **aeiah said:**
> or better still (if you cant get zoneminder to stop leaking), why not run a cronjob every 5 minutes that monitors your system's memory, and when it gets really high it restarts zoneminder/apache?
That's a great idea.  I currently have it set to restart apache every hour.  There are two problems with this.  (1) if it's working and someone is viewing the camera, restarting apache freezes things until the site is refreshed. (2) If it is not working, you have to wait until Apache restarts to view.  The coding behind the script doesn't seem that hard.  Find the minimum level, get the ram usage, compare to that level & process if it exceeds that base.  It is not resource intensive or intrusive.

I still want to look into the other stuff you guys talked about.  They seem like cool tools to know.

---

