---
title: "Bring up GUI of networked system on another system?"
date: 2009-07-12
forum: General Help
---

### Post by TheForkOfJustice on 2009-07-12
My system is connected to another system (my fileserver) by SSH over a network.

I need to connect a printer to my fileserver because my main lacks the necessary parallel port connection.

Can I hook up my printer via SSH from my main system and can my main system, in turn, use it to print stuff?

Can I access my fileserver's desktop from my main over SSH and use the GUI to easily set the printer up?

I don't want to go through the trouble of swapping peripherals.

Advice?

---

### Post by LepeKaname on 2009-07-12
1) Connect your printer to your fileserver
2) Enter to your fileserver and allow in CUPS remote management.
3) Enter to CUPS control panel (from your main computer): 

[http://fileserver:631/](http://fileserver:631/) (change fileserver for the IP)

4) Add the printer
5) Setup your main computer to use that network printer

There are plenty of tutorials (I guess) about that. Its not that difficult as it may look. If you still have problems, let us know.

If you don't want to allow the remote management (2):

2) Enter to your fileserver and install x11vnc. 
3) Login in X (you must have an active X session) at your fileserver. 
4) Run in the fileserver: x11vnc -unixpw -display :0 
5) Install some vnc client in your main 
6) Connect to your fileserver desktop through vnc client :)
7) Intall the printer via: [http://localhost:631/](http://localhost:631/)
8 ) Setup your main computer to use that network printer

good luck!

---

### Post by TheForkOfJustice on 2009-07-12
I'm stuck on number 2.

How do I let in CUPS remote management?

---

### Post by LepeKaname on 2009-07-12
First, you need to change the listen IP (default: 127.0.01), to your local IP (e.g. 192.168.0.2) ([check this]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html"))

Then, edit: /etc/cups/cupsd.conf. This is just an example, I'm not sure if it will work for you... search on "enable remote administration".

> # Restrict access to the server...
<Location />
Order allow,deny
Allow localhost
</Location>

# Restrict access to the admin pages...
<Location /admin>
Encryption Required
Order allow,deny
Allow 192.168.0.0/24
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
AuthType Basic
Require user @SYSTEM
Order allow,deny
Allow 192.168.0.0/24
</Location>

# Set the default printer/job policies...
<Policy default>
# Job-related operations must be done by the owner or an adminstrator...
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set$
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

# All administration operations require an adminstrator to authenticate...
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Dis$
AuthType Basic
Require user @SYSTEM
Order deny,allow
</Limit>

# Only the owner or an administrator can cancel or authenticate a job...
<Limit Cancel-Job CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

<Limit All>
Order deny,allow
</Limit>
</Policy>

Restart CUPS.

Don't forget to enable port 631 if you are using a firewall.

---

### Post by TheForkOfJustice on 2009-07-12
Still having trouble.  Not sure what is the issue.

Be back tomorrow night.

---

### Post by TheForkOfJustice on 2009-07-14
Bought new printer. Canon Pixma iP2600

Works on Vista but not so well on Linux yet.

And I just broke my Windows install.

Ain't that grand?

---

### Post by LepeKaname on 2009-07-14
Check this thread:

[http://ubuntuforums.org/showthread.php?t=811811](http://ubuntuforums.org/showthread.php?t=811811)

They managed to install the "Canon Pixma iP2600" printer.

You need to enter to your fileserver, install and test your printer locally (just in that computer). Then if everything goes fine, try to grant access so any other computer in the same network can print through it.

---

### Post by TheForkOfJustice on 2009-07-20
Something wrong with the driver.

Printer is detected but the paper won't feed.  Works fine on Windows.

I'll re-test it later.

---

