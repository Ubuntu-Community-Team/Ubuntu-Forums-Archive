---
title: "What is this in my terminal"
date: 2009-12-26
forum: General Help
---

### Post by sigurnjak on 2009-12-26
When i start my terminal it starts with this :


--2009-12-26 10:37:18--  [http://0161.t35.com/index.php](http://0161.t35.com/index.php)
Resolving 0161.t35.com... 66.45.237.212, 69.10.48.106
Connecting to 0161.t35.com|66.45.237.212|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.php.3'

    [ <=>                                   ] 2,235       --.-K/s   in 0.009s  

2009-12-26 10:37:18 (243 KB/s) - `index.php.3' saved [2235]

andrey@andrey-desktop:~$ PING [www.leetcoders.org](www.leetcoders.org) (74.208.192.19) 65507(65535) bytes of data.


What is it and how do i remove it ?

---

### Post by CharlesA on 2009-12-26
Looks like it's running wget and then pinging  a site. Probably trying to DoS the site.

Did anything change on yer system recently?

---

### Post by scouser73 on 2009-12-26
I've just gone to [http://0161.t35.com/](http://0161.t35.com/) and it's a web hosting site.

[IMG]http://0161.t35.com/[/IMG]

---

### Post by sigurnjak on 2009-12-26
I downloaded this and try to run it :
[http://www.gnome-look.org/content/show.php/QStars?content=117099](http://www.gnome-look.org/content/show.php/QStars?content=117099)

Am i hacked ? Socially engineered scam maybe ?

What now ?

---

### Post by __p1n__ on 2009-12-26
> **sigurnjak said:**
> When i start my terminal it starts with this :


--2009-12-26 10:37:18--  [http://0161.t35.com/index.php](http://0161.t35.com/index.php)
Resolving 0161.t35.com... 66.45.237.212, 69.10.48.106
Connecting to 0161.t35.com|66.45.237.212|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.php.3'

    [ <=>                                   ] 2,235       --.-K/s   in 0.009s  

2009-12-26 10:37:18 (243 KB/s) - `index.php.3' saved [2235]

andrey@andrey-desktop:~$ PING [www.leetcoders.org]("http://www.leetcoders.org") (74.208.192.19) 65507(65535) bytes of data.


What is it and how do i remove it ?

 You're pwned.  Wipe the disk and reinstall from media (verify the media checksum before you do this.)  Also, don't set up the vnc and/or ssh server which are the odds-on favorites for how your box got infected.

---

### Post by scouser73 on 2009-12-26
Before you wipe anything, wait for a better answer from someone with experience of this.  It may not be as bad as it seems.

---

### Post by sigurnjak on 2009-12-26
Would clam scan help ? Also when i back up , should i just back up my personal files and skip any config files ? Also any tips are appreciated . Also , i do not mind wipe  since most of my files are on external drive .

---

### Post by scouser73 on 2009-12-26
Well you should remove the screensavers that you've downloaded firstly, then run a scan with ClamAV and see what the results are, then search the forums for other instances of this and see what the procedure is.

---

### Post by taurus on 2009-12-26
While the terminal is still opened, click the right button with the cursor in the terminal and pick Profiles -> Profile Preferences.  What does it say in the Title and Command?

---

### Post by sigurnjak on 2009-12-26
Here is a screenshot of termial profile  if it helps .I did delete screensaver already and php.index it creates .
And here is output of file it creates :

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
<a target=_blank href=http://www.sunglassessale.co.uk/collections/womens-sunglasses/>Womens Sunglasses</a>&nbsp;-&nbsp;<a target=_blank href=http://www.hypercasinos.com/content/category/1/1/2/>Casino News</a>&nbsp;-&nbsp;<a target=_blank href=http://www.mckennavw.com>Volkswagen Dealer</a>&nbsp;-&nbsp;<a target=_blank href=http://www.drugrehabcenter.com/>Treatment Center</a>&nbsp;-&nbsp;<a target=_blank href=http://www.bestonlinecollegesdegrees.com>Best Online College</a>&nbsp;-&nbsp;<a target=_blank href=http://www.uk-cheapest.co.uk>Hosting</a>&nbsp;-&nbsp;<a target=_blank href=http://www.fashiondrops.com/>Prada</a>&nbsp;-&nbsp;<a target=_blank href=http://www.citygrounds.com>Fixed Gear Bike</a>
</div>

Maybe this helps someone with more skill then me .

---

### Post by taurus on 2009-12-26
Reboot.  Then open gnome-terminal again after you've logged back in.

---

### Post by bkratz on 2009-12-26
> **taurus said:**
> While the terminal is still opened, click the right button with the cursor in the terminal and pick Profiles -> Profile Preferences.  What does it say in the Title and Command?



It sort of looks like the same stuff that was in this  (please verify, I don't want to scare anyone--even me!) with the T35.com stuff


[http://ubuntuforums.org/showthread.php?t=1349678&highlight=gnome-look](http://ubuntuforums.org/showthread.php?t=1349678&highlight=gnome-look)

---

### Post by audiomick on 2009-12-26
+1 bkratz

---

### Post by sigurnjak on 2009-12-26
I have just created new account on my pc and tried terminal there and it looks clean . I will try migrating my stuff to new account and erasing my old account .  It looks as if only my account has been messed up . Ah , beauty of Linux !:)

---

### Post by audiomick on 2009-12-26
Hallo.
Did you read right through the thread that bkratz linked to?
There is info on removing in post #20 , #37, #47 , #50 and maybe some others. I stopped looking at 50.

It might be easier to try that first, before you try and migrate to a new user.

---

### Post by sigurnjak on 2009-12-27
I tried  and there is no such file anywhere . I looked  in that tread and did not find anything to  that was on my machine . 
On the  other hand Santa was nice so i get to actually move everything to a new sata drive instead of my old IDE drive  . :)

---

