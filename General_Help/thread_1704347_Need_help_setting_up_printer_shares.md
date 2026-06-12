---
title: "Need help setting up printer shares"
date: 2011-03-10
forum: General Help
---

### Post by WinterMadness on 2011-03-10
I have my printer setup with a ubuntu machine, and I want the windows machines to be able to print with that printer as well.

I have samba setup, everything is default
the printer works, ive used it, I just cant print over the network

help? :)

I seem to find very out of date tutorials as well.

Im running ubuntu 10.10 using gnome

When I goto my windows machine and type 192.168.1.9:631 I am able to see the cups webpage.

thanks

---

### Post by tordeu on 2011-03-10
A good starting point is [https://help.ubuntu.com/10.10/serverguide/C/cups.html](https://help.ubuntu.com/10.10/serverguide/C/cups.html).

I am not really good when in comes to CUPS, but I just wanted to let you know what I did to use share printer from an Ubuntu Server 10.10 with a Windows XP machine. I hope this can help in any way (what I did is taken mostly from the link above):

[COLOR=Red]EDIT: Just noted your comment about already having CUPS running. If you have already set up your printer successfully in CUPS, start with step 7.[/COLOR]

1. install CUPS:
```
sudo apt-get install cups
```2. backup the conf file and make it write protected (this is optional, but a good idea):

```

sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf.original
sudo chmod a-w /etc/cups/cupsd.conf.original

```3. edit the conf file with an editor. if you know nano, just do
```

sudo nano /etc/cups/cupsd.conf

```or if you want a graphical editor, you can use gedit:
```

sudo gedit /etc/cups/cupsd.conf &

```Find the lines which start with "Listen". If they do not exist (I think there is at least one), look for the line "# Only listen for connections from the local machine".

Edit this section, so it looks like this:
```

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

```Save the edited file now.

4. Restart CUPS:
```
sudo /etc/init.d/cups restart
```5. add your user to the lpadmin:

```
sudo usermod -aG lpadmin <yourusername>
```Now, you should be done with this part.

6. Now you need to add your printer to CUPS. Open a browser and go to

localhost:631

This is the web interface of CUPS. Click on "Administration", there you can add your printer or let it automatically detect it. Make sure the printer is turned on and connected to the machine.

7. When the printer is added, click on "Printers" in the top menu bar. This is where your printers are listed. Note the "query name" and write it down (My Ubuntu machine automatically could use the CUPS printer I have hooked up to a server, but for the Windows XP machine I added I needed this query name).

In my case, for example, the query name was "Samsung_ML-3470_Series".

8. In Windows (at least in XP) you now need to add a network printer and use the following as a network address:
http://<IPADDRESS>:631/printers/<QUERYNAME>

The IP address is the IP of the machine to which the printer is connected and the "query" name
if the query name which was shown in CUPS.

You should now be able to print.

---

