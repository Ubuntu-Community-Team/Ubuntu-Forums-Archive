---
title: "Howto: Keep an external weblink pointed at your local dynamic IP"
date: 2009-07-05
forum: General Help
---

### Post by dwasifar on 2009-07-05
Okay, I'm not sure how much need there is for this, but I had to solve the problem for myself so I figured I'd share it in case anyone else needs it.  It could be useful for remote access to one's home network, or running one's own "circumventor" type web proxy, for example.

I have a couple of domains hosted with an external hosting service.  I don't host them myself because the external hosting is cheaper than paying my ISP for a static IP.  But occasionally I do need to connect to my local network remotely.  This is where the ISP's dynamic IP is an inconvenience.  So I set up a process that maintains a redirecting weblink on one of the externally hosted domains, pointing to whatever my home connection's dynamic IP currently is.  Here is how to do it.

1) Install ncftp on your local machine.  It's in the repos:
```
sudo apt-get install ncftp
```

2) Open a text editor and paste in the following script:
```
#!/bin/sh
cd ~/
mv redirect.html redirectold.html
IPADR=$(wget www.whatismyip.com/automation/n09230945.asp -O - -q)
if [ "$IPADR" != '' ]; then
echo "<html><head><title>Weblink redirect</title><meta http-equiv=\"REFRESH\" content=\"0;url=http://""$IPADR""/\"></HEAD><BODY></BODY></HTML>" > redirect.html
DIFFOUT=$(diff -N redirectold.html redirect.html)
if [ "$DIFFOUT" != '' ]; then
FTPU="login_name" # ftp login name
FTPP="login_pass" # ftp password
FTPS="ftp.yourdomain.com" # remote ftp server
FTPF="/html/" # remote ftp server directory where the file will be uploaded
LOCALD="~/redirect.html"
ncftpput -m -u $FTPU -p $FTPP $FTPS  $FTPF $LOCALD
fi
fi
```

3) Replace the ftp connection information in the above with your remote server's login and path information.  (Optionally you can also change the name of the file "redirect.html" to something else that suits you better.)

4) Save the script, without extension, to one of the /etc/cron directories.  I have mine in /etc/cron.hourly so it runs every hour.  

5) Give the script root ownership and root group and set it executable.

Each time it runs, the script will update the file "redirect.html" on the remote domain so that it contains the local machine's current IP.  Wherever you are, [http://[yourdomain.com]/redirect.html](http://[yourdomain.com]/redirect.html) will instantly redirect you to your own home IP.  

(If you need it to run more often than hourly, you could always set up a specific cron job to do it.  If I were going to run it more frequently I'd probably modify it to only upload if the IP changed from the previous run.)

Edit: I couldn't leave well enough alone.  I modified the script so that it backs up the previous version of the html file and then checks for changes before uploading; if no change, no upload.  Now you can schedule the script to run every couple of minutes without generating a lot of redundant uploads.

Edit: I just found out whatismyip.com doesn't want you to hit their automation script any more frequently than 300 seconds, so don't schedule this script more often than every 5 minutes.

---

### Post by prshah on 2009-07-05
> **dwasifar said:**
> 
I have a couple of domains hosted with an external hosting service.  

...and for those of you who don't have externally hosted domains, but still need remote access to your machines, you have the option to install the "ddclient" or "dyndns-client" programs, which will allow you to update your IP address at your dyndns redirector.

And, of course, most modern (router/adsl modems) include options for DynDNS.

The script above is good, these are just alternatives.

---

### Post by dwasifar on 2009-07-05
> **prshah said:**
> ...and for those of you who don't have externally hosted domains, but still need remote access to your machines, you have the option to install the "ddclient" or "dyndns-client" programs, which will allow you to update your IP address at your dyndns redirector.

And, of course, most modern (router/adsl modems) include options for DynDNS.

The script above is good, these are just alternatives.

You know, I didn't even think of DynDNS for doing this.  You're right, that would work too.  Except at the moment it seems to be down.  At least their website is down.

I wish I could query my Linksys router directly for the IP, rather than rely on an external service like whatismyip.com.  Seems like there should be a command that queries the router for that info.

---

### Post by mbeach on 2009-07-05
I could be wrong but I think that these folks have got a script which is able to grab the ip from a bunch of different routers. If your's isn't supported, you may be able to alter accordingly.

[http://ipcheck.sourceforge.net/](http://ipcheck.sourceforge.net/)

good luck,
mb

---

### Post by t4thfavor on 2009-07-05
I run the ddns client on my Linksys router. and it does it for me. I never ever have to mess with it, and its always correct.

---

### Post by dwasifar on 2009-07-06
> **mbeach said:**
> I could be wrong but I think that these folks have got a script which is able to grab the ip from a bunch of different routers. If your's isn't supported, you may be able to alter accordingly.

[http://ipcheck.sourceforge.net/](http://ipcheck.sourceforge.net/)
It does pull the IP from the router, but rather than returning it to the user, it just uses it to update DynDNS.  

Still, what I want to do is obviously somewhere in that script.  It'll be a good opportunity to learn about Python.  Thanks for the link.

---

### Post by mbeach on 2009-07-07
For the fun of it, I dug out my linksys (WRT54G).

if you use a wget like
```
wget http://linksysusername:linksyspassword@192.168.0.2/StaRouter.htm
```

it will save the file which contains the IP address.

Combine that wget with a pipe to grep or awk combo (there are some experts around here) to parse the important bit and I'm sure you'll be able to get your ip address.

For the record, the StaRouter.htm file contains a line or two like this (in this case 0.0.0.0 is the ip).
```

          <TD><FONT style="FONT-SIZE: 8pt"><script>Capture(share.ipaddr)</script>:</FONT></TD>

          <TD><FONT style="FONT-SIZE: 8pt"><B>0.0.0.0</B></FONT></TD>

```

---

### Post by mbeach on 2009-07-07
I thought that
```

sed -n '/ipaddr/ {n;p;}' StaRouter.htm | sed -n '/<B>/,/<\/B>/ p'

```
would work, but I'm missing something obvious with that second sed as the whole line is returned, not just what is between the B tags.

---

### Post by mbeach on 2009-07-07
This seems to work for the linksys WRT54G (in my case it has internal ip of 192.168.0.2)

```

wget -q -O- http://admin:linksyspassword@192.168.0.2/StaRouter.htm | sed -n '/ipaddr/ {n;p;}' | sed -e 's/.*<B>//; s/<\/B>.*//'

```

---

### Post by dwasifar on 2009-07-09
> **mbeach said:**
> This seems to work for the linksys WRT54G (in my case it has internal ip of 192.168.0.2)

```

wget -q -O- http://admin:linksyspassword@192.168.0.2/StaRouter.htm | sed -n '/ipaddr/ {n;p;}' | sed -e 's/.*<B>//; s/<\/B>.*//'

```

Nice!

For my router I had to change the page it was looking at to Status_Router.asp, but other than that it is perfect.  Thanks!

---

### Post by HotForLinux on 2009-07-13
[dwasifar]("http://ubuntuforums.org/member.php?u=59966"):

I can't help but it seems that what would be nicer is to detect your "home IP" right at the server of your web hosting provider. That would amount to do the job whatismyip.com is doing for you. You'll probably be able to find a cgi-script that does this. The bad side is that you'll need to protect the access to this  script so that only you can access it. All that would amount to do what the DynDNS servces are doing for you but you'll do it with your domain_name.

---

### Post by mbeach on 2009-07-21
> **dwasifar said:**
> Nice!
... but other than that it is perfect.  Thanks!

Good I'm glad it worked for you. It was a fun problem to take a look at.

---

