---
title: "Host a website on my home PC"
date: 2009-07-15
forum: General Help
---

### Post by nikhilbhardwaj on 2009-07-15
hi 
i know that there are many guides on the internet and i have tried to follow almost all
but what happens in the end is that i am redirected to my routers page instead of my website.

i have an dynamic ip assigned to me by my isp.
its start page is 192.168.1.1
my external ip as i post is 59.xxx.xx.xx
this too akes me to my routers sire

i've tried to use portforward.com
and no-ip.org to no avail

help will be much appreciated
btw i'm running apache to host the site

---

### Post by t4thfavor on 2009-07-15
remove your IP!! pronto!!!

For real Do it now!

Login to your router, and look for something called Virtual Server, and then forward the correct port from the outside to the web host on the inside. Currently your router is accepting port 80 requests instead of forwarding them to an internal host, you will either have to remove the remote administration feature, or change the port Apache runs on.

---

### Post by nikhilbhardwaj on 2009-07-15
what harm could it do
it cant access my pc can it

but i'll do so if you insist

---

### Post by t4thfavor on 2009-07-15
your router has a default password and username, it was about 5 seconds before I logged into it.

Its how I noticed that your going to have to look for Virtual Server.

With that info I could steal your ISP info, or shut off your internet access, not to mention open up whatever port I wanted to so that I could then launch an attack against you on that port.

Not a good idea to post your real IP ever. (unless you are sure of your security)

---

### Post by nikhilbhardwaj on 2009-07-15
OH MY GOD
is this for real!!!
could you really do this

phewwww........


these are the options
which ones should i change
Private IP:       
Protocol:   ANY
 
Local Port:
Destination Port From:  to

---

### Post by t4thfavor on 2009-07-15
So your internal webserver has a 192.168.1.x address, make it so that your virtual server host is that ip address, and then change the port to something like 8080. on the outside and 80 on the inside. 

Your router may not be able to change the external port, so you may have to change the listen port of apache to the same as what it is on the outside.

Also change the password on your router while your in there.

Oh, yeah, This is for real.

Should look something like this 

Private IP = 192.168.1.whatever
protocol = TCP
local Port = 80 maybe switch with below?
destination port 8080
single port

---

### Post by nikhilbhardwaj on 2009-07-15
ok
i've configured apache to listen to 8080
and did as you said
but still get redirected to the router page

[http://192.168.1.x:8080](http://192.168.1.x:8080) works
but 59.xxx.xx.xx:80 or 8080 doesn't
have tried shifting the port values

---

### Post by prem1er on 2009-07-15
Did you restart Apache after you made the change?

---

### Post by t4thfavor on 2009-07-15
Restart Apache
```

sudo /etc/init.d/apache restart

```

then make sure that the port forward has 8080 in both the local port, and the destination port.

---

### Post by nikhilbhardwaj on 2009-07-15
yes i've restarted apache
and can access it locally with localhost:8080

also made both the ports 8080

---

### Post by aesis05401 on 2009-07-15
This is fun.

I'm pulling for you nikhilbhardwaj.

---

### Post by prem1er on 2009-07-15
If you can access it locally on that port, than the problem is still in the router.

Edit: Sorry didn't mean to jack the thread I will stop now.

---

### Post by nikhilbhardwaj on 2009-07-15
> **aesis05401 said:**
> This is fun.

I'm pulling for you nikhilbhardwaj.

whats that supposed to mean:p

---

### Post by nikhilbhardwaj on 2009-07-15
> **prem1er said:**
> If you can access it locally on that port, than the problem is still in the router.

Edit: Sorry didn't mean to jack the thread I will stop now.

i dont mind 
if you can help me too thats great

---

### Post by y@w on 2009-07-15
Is there an apply settings button in the router somewhere that you missed maybe?

---

### Post by t4thfavor on 2009-07-15
Maybe you have to reboot the router. Also it may not work for you inside by using your router's external IP you need something called NAT loopback in order for that to work, and I don't believe your router has that feature.

---

### Post by nikhilbhardwaj on 2009-07-15
ok
i'll reboot the router and let you know what happens

---

### Post by hitman_dreams on 2009-07-15
Boy you're lucky people in here are helpful...

---

### Post by aesis05401 on 2009-07-15
> **nikhilbhardwaj said:**
> whats that supposed to mean:p

I'm pulling for you means I am wishing you the best of luck in your endeavor.

More specifically, though:
It means that I hope you succeed in this implementation, I hope your website is very popular, I hope you learn interesting things while implementing this website, **but most of all, I hope you start doing a lot of security reading**. These forums are a good place to start.

The cloud is a dangerous place.  It makes me feel good about this forum community to see how quickly another user moved to inform you of an error that could have resulted in a bit of mayhem for you.

Best of luck, and always have a backup image ready to go ;)

---

### Post by nikhilbhardwaj on 2009-07-15
> **hitman_dreams said:**
> Boy you're lucky people in here are helpful...

i agree with you 100%
these people are AWESOME

---

### Post by nikhilbhardwaj on 2009-07-15
> **aesis05401 said:**
> I'm pulling for you means I am wishing you the best of luck in your endeavor.

More specifically, though:
It means that I hope you succeed in this implementation, I hope your website is very popular, I hope you learn interesting things while implementing this website, **but most of all, I hope you start doing a lot of security reading**. These forums are a good place to start.

The cloud is a dangerous place.  It makes me feel good about this forum community to see how quickly another user moved to inform you of an error that could have resulted in a bit of mayhem for you.

Best of luck, and always have a backup image ready to go ;)

ya i know you are right
will be more careful in the future
thanks

---

### Post by t4thfavor on 2009-07-15
Its because I'm fast like a marsupial! While were waiting, I have to ask, Whats that creepy hexagon thingy in the center of New Delhi? Thats some crazy city design.

This is directed at
nikhilbhardwaj

How did the router reboot go?

---

### Post by nikhilbhardwaj on 2009-07-15
so this is what happened
i powered off my router and then powered it on again
now when i logged onto it

the virtual servers list is cleared

now i've added it again
Virtual Servers List#Private IPProtocolPrivate PortPublic Port 1192.168.1.3TCP80808080[URL="http://192.168.1.1/MainPage?id=52&rule_id=4"]
[/URL]
any clue as to why that happens
i did apply after adding it and it has been added to the list
but when i reboot the router
the list gets cleared 
WHY???

---

### Post by t4thfavor on 2009-07-15
Crappy router possibly? I didnt catch a model number, but I bet it needs something to make it stick other than an apply.

---

### Post by nikhilbhardwaj on 2009-07-15
> **t4thfavor said:**
> Crappy router possibly? I didnt catch a model number, but I bet it needs something to make it stick other than an apply.

should i give you the new dynamically assigned ip address again
so that you can get whatever info you need

---

### Post by aesis05401 on 2009-07-15
> **t4thfavor said:**
> Crappy router possibly? I didnt catch a model number, but I bet it needs something to make it stick other than an apply.

Old school trick from the early days of routers w/html admin interfaces: If it doesn't stick through the GUI then log into the service port and try with the command line. 

Every major American router company I know of shipped consumer grade routers with incomplete GUI admin features back in the 1990's... but the underlying CLI was complete because the developers needed it.

---

### Post by t4thfavor on 2009-07-15
Has the IP changed, I still have it just in case you want me to take a look.

---

### Post by nikhilbhardwaj on 2009-07-15
> **aesis05401 said:**
> 
Every major American router company I know of shipped consumer grade routers with incomplete GUI admin features back in the 1990's... but the underlying CLI was complete because the developers needed it.

i dont know enough command line to add that rule to the router
i'm in india 
the router may well be american i'm not sure

the number on the box is T-KD 318-EUI

---

### Post by nikhilbhardwaj on 2009-07-15
> **t4thfavor said:**
> Has the IP changed, I still have it just in case you want me to take a look.

yes 
_**xxxxxxx**_


please take a look at it

i'll remove this as soon as you get it

---

### Post by t4thfavor on 2009-07-15
use pm for ip

---

### Post by t4thfavor on 2009-07-15
Working

Access forbidden!

New XAMPP security concept:

Access to the requested directory is only available from the local network.

This setting can be configured in the file "httpd-xampp.conf".

If you think this is a server error, please contact the webmaster.
Error 403

Thursday 16 July 2009 12:46:26 AM EDT
Apache/2.2.11 (Unix) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8k PHP/5.2.9 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0

---

### Post by nikhilbhardwaj on 2009-07-15
i dont get that output

where is this file
theres http.conf in /opt/lampp/etc/

this doesn't seem to be there

found it
its in /opt/lampp/etc/extra

---

### Post by t4thfavor on 2009-07-15
hrm, thats what I get when I put in the IP you gave me
[http://xx.xx.xx.38:8080/](http://xx.xx.xx.38:8080/)
redirects me to 

[http://xx.xx.xx.38:8080/xampp/](http://xx.xx.xx.38:8080/xampp/) and gives me that error. Maybe try some off the wall port like 64544 it should be open. 8080 works here in US, but the ISP in India may be doing something on that port.

---

### Post by nikhilbhardwaj on 2009-07-15
this is the section in the file

#
# New XAMPP security concept
#
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-st$
        Order deny,allow
        Deny from all
        Allow from ::1 127.0.0.0/8 \
                fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 \
                fe80::/10 169.254.0.0/16

        ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>

what changes should i make to that

---

### Post by t4thfavor on 2009-07-15
Allow from ::1 0.0.0.0/24 should work

or 

Allow from all since you want this to be public.

I think the other crap is just ip6 stuff.

End result should read something like this.

```

#
# New XAMPP security concept
#
<LocationMatch "^/(?i?ampp|security|licenses|phpmyadmin|webalize r|server-st$
Order deny,allow
#Deny from all
Allow from all

ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>


```

---

### Post by nikhilbhardwaj on 2009-07-15
i went to hideyass.com
and put that url

i got the same message as you so should i now change the port to something else
or will changing the file httpd-xampp do it

---

### Post by t4thfavor on 2009-07-15
looks like your good, its working from here, the rest is just permissions on the webserver (edit the file, and restart the webserver to find out)

I just realized something:

Whats it like to be in tomorrow, today :)
Thursday 16 July 2009 01:04:00 AM EDT

---

### Post by nikhilbhardwaj on 2009-07-15
try this

[http://59.177.xx.xx:8080:/tmp/index.php]("http://59.177.71.38:8080:/tmp/index.php")

yup
you correct you are
thanks a lot

now i've got to figure out why it gets removed when i reboot
but thats for another time

its 1:07 am here
gotta get to bed

once again
thankyou very much
you've been prompt and helpful and informative

cant thank you enough i guess
bbye

---

### Post by t4thfavor on 2009-07-15
NP, Glad to help, Nice website...

---

