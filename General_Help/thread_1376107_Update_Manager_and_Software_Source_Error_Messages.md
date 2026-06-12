---
title: "Update Manager and Software Source Error Messages"
date: 2010-01-08
forum: General Help
---

### Post by genesisleighton883BC on 2010-01-08
(Note: I apologize for the length in advance.)

[FONT=Arial][SIZE=2][I]Two days I ago I installed -well, tried to-  Microsoft Office 2007 (I had WINE previously installed on my computer). I try to open up Word and it works fine until I tried to save something and the program shut itself down. Tired again, same thing. I then tried to open Acess and then OneNote wondering if it was just Word. It wasn't. The two latter programs wouldn't even open properly. 
[/I][/SIZE][/FONT]
[FONT=Arial][SIZE=2][I]   I uninstalled WINE, downloaded it again, installed it a second time. This time with WineTricks included.Nothing Microsoft realted opened fully (on the taskbar it showed it was trying to open, their little yellow screen popped up, said that MS Office wasn't installed for this user -and I'm the only user on this computer- and then the whole thing disappeared). I discovered I could not remove MS Office from my computer at all. 
[/I][/SIZE][/FONT]

[FONT=Arial][SIZE=2]*   When I booted up my computer today my update-manager popped up with a message: *[/SIZE][/FONT]
[B][FONT=Arial][SIZE=2]
[/SIZE][/FONT][/B]
**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Line 1 too long in source list /etc/apt/sources.list.d/winehq.list., E:The list of sources could not be read.'[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
    *I am, needless to say, concerned seeing as I *have* to use MS Office for my school work for college. So, I started looking around the forum and on other places on the internet to see if anyone else had a similar issue. I found a few things but when I tried them they didn't work or there was not a following step.*





[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]*In other threads it was suggested to use the *  cat /etc/apt/sources.list *command in the terminal when I did I got:*

[/SIZE][/FONT]
[FONT=Microsoft Sans Serif][SIZE=2]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]# newer versions of the distribution. [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]## Major bug fix updates produced after the final release of the [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## distribution. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## team. Also, please note that software in universe WILL NOT receive any [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## review or updates from the Ubuntu security team. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## team, and may not be under a free licence. Please satisfy yourself as to  [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## your rights to use the software. Also, please note that software in  [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## multiverse WILL NOT receive any review or updates from the Ubuntu [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## security team. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]## Uncomment the following two lines to add software from the 'backports' [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## repository. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## N.B. software from this repository may not have been tested as [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## extensively as that contained in the main release, although it includes [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## newer versions of some applications which may provide useful features. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## Also, please note that software in backports WILL NOT receive any review [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## or updates from the Ubuntu security team. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]## Uncomment the following two lines to add software from Canonical's [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## 'partner' repository. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## This software is not part of Ubuntu, but is offered by Canonical and the [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]## respective vendors as a service to Ubuntu users. [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner [/SIZE][/FONT]
 
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse [/SIZE][/FONT]
 [FONT=Microsoft Sans Serif][SIZE=2]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]*When I tried to change the sourcs on Software Sources I got this:*
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 
**[FONT=Arial][SIZE=2]Could not download all repository indexes :[/SIZE][/FONT]**
 
 [FONT=Arial][SIZE=2]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 *[FONT=Arial][SIZE=2]Immediately followed by:::[/SIZE][/FONT]*
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 **[FONT=Arial][SIZE=2]An Error occurred:[/SIZE][/FONT]**
 [FONT=Arial][SIZE=2]E: Line 1 too long in source list /etc/apt/sources.list.d/winehq.list. [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]E: Unable to lock the list directory[/SIZE][/FONT]
 

*and:::*

[FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 **[FONT=Arial][SIZE=2]An Error occurred:[/SIZE][/FONT]**
 [FONT=Arial][SIZE=2]E: Line 1 too long in source list /etc/apt/sources.list.d/winehq.list. [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]E: The list of sources could not be read. [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Go to the repository dialog to correct the problem. [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]E: _cache->open() failed, please report.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]*Uh, *help*? I'm sort of starting to panic about this. I have no idea what to do now or what the heck is going on with my computer. Any ideas or fix - it suggestions?*
[/SIZE][/FONT]

---

### Post by zvacet on 2010-01-08
> 'E:Line 1 too long in source list /etc/apt/sources.list.d/winehq.list.

```
cat /etc/apt/sources.list.d
```

and post output here.

---

### Post by ibuclaw on 2010-01-08
> **zvacet said:**
> ```
cat /etc/apt/sources.list.d
```

and post output here.

I think you mean:
```
cat /etc/apt/sources.list.d/winehq.list
```
and post the output here.

---

### Post by genesisleighton883BC on 2010-01-08
*Ok, here' it is:::*


root@leighton-laptop:/home/rogue# **cat /etc/apt/sources.list.d**
cat: /etc/apt/sources.list.d: Is a directory
root@leighton-laptop:/home/rogue#_** cat /etc/apt/sources.list.d/winehq.list**_
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"><html xmlns="http://www.w3.org/1999/xhtml"><head><title>CenturyLink Search Guide</title><meta http-equiv="content-type" content="text/html; charset=UTF-8"><meta http-equiv="Pragma" content="no-cache"><meta http-equiv="Expires" content="-1"><meta name="robots" content="nofollow"><meta http-equiv="X-UA-Compatible" content="IE=7" /><ie:homepage id="homepage" style="behavior:url(#default#homepage)"><link title="CenturyLink" rel="search" type="application/opensearchdescription+xml" href="/add_search.php"/><link rel="shortcut icon" href="favicon.ico"><link rel="stylesheet" type="text/css" media="screen" href="./css/core_nxd.css" /><!--[if IE]><link rel="stylesheet" type="text/css" media="screen" href="./css/ie_core_nxd.css" /><![endif]--><!--[if IE 6]><link rel="stylesheet" type="text/css" media="screen" href="./css/ie6_core_nxd.css" /><![endif]--><script type="text/javascript">var phrase_orig = 'list ';var phrase_one = 'Type Your Search Here';var phrase_two = 'Please, Type Your Search Here';var hostname = 'http://search.centurylink.com';var ref_search = '';</script><script src="./js/common_jscript-min.js" type="text/javascript"></script></head><body>    <div id="whatsthis" style="left: 0px; display: none;">
        <div class="whatsthisbody">
            <a class="close" href="#" onclick="toggleDetails('whatsthis', event);return false;"><img src="./img/close_button.jpg"/></a>
            <div class="wttitle">Why am I here?</div>
            <p>The CenturyLink redirection service has been enabled to provide helpful searches from web address errors. You entered an unknown name that the CenturyLink service used to present site suggestions which you may find useful. Clicking any of these suggestions provides you with Yahoo! search results, which may include relevant sponsored links.</p>
            <div class="wttitle">Can I opt out of this service?</div><p>If this service is not right for you, please visit your <a href="prefs.php">Preferences</a> page to opt out. At any point in time, you can opt back in to the service by visiting your <a href="prefs.php">Preferences</a> page.</p>
            <div class="wttitle">What if I still have questions?</div>
            <p>If you have other questions about this service, please visit our <a href="faq.php">FAQ</a></p>
        </div>
        <div class="whatsthisbottom">&nbsp;</div>
    </div><div class="upper_menu"><span><span id="box_HomePage" style="display:none;"></span></span><a href="http://www.centurylink.com">CenturyLink.com</a><span class="mDD"><img src="./img/arrow.png"/><div class="dd"><div><a href="http://www.centurylink.com">Residential</a></div><div><a href="http://www.centurylink.com">Business</a></div><div><a href="http://www.centurylink.com">Wholesale</a></div><div><a href="http://www.centurylink.com/MyAccount/ma.html">MyAccount</a></div><div><a href="http://www.centurylink.com/Pages/Support">HSI Support</a></div></div></span><a href="faq.php">F.A.Q.</a><span class="why"><a href="#" class="whyamihere" onclick="pageCon.make_WhatsThis(event);return false;" title="More Details">Why am I here?</a><div id="whatsthis" style="left: 0px; display: none;"></div></span></div><div class="top_form"><form action="index.php" name="headersearchform" id="headersearchform" class="searchForm"><table border="0" cellpadding="0" cellspacing="0"><tr valign="top"><td class="logo"><a href="http://www.centurylink.com"><img src="./img/logo_top_home.png" alt="logo"/></a></td><td class="centerCell"><div id="search_box_left_image"><img src="./img/search_box_background_left.jpg"/></div></td><td class="centerCell"><div class="inputHolder"><input type="text" size="40" id="queryBoxTop" class="queryBox" name="search" value="list "/></div><div id="suggestionBox" style="display: none;height: 1px;"><table cellpadding="0" cellspacing="0" border="0"><tr valign="top"><td id="suggestionBoxLeft" style="height: 1px;">&nbsp;</td><td id="suggestionBoxText" style="height: 1px;"></td><td id="suggestionBoxRight" onmousedown="drag('suggestionBox',event)" style="height: 1px;">&nbsp;</td></tr></table></div></td><td class="centerCell"><input type="submit" name="submit" value="Web Search" class="button" size="50px" id="buttonheadersearchform" style=""/></td><td class="centerCell"><span id="buttonRightheadersearchform" style="margin-left:0em;"><img src="./img/search_box_button_right.jpg" class="button_right"/></span></td></tr></table></form></div><div class="welcome">CenturyLink Search Guide</div><center><table id="suggestion_table" cellpadding="0" cellspacing="0"><tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Travel">Travel</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Financial+Planning">Financial Planning</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=E+Commerce">E Commerce</a></td></tr>
<tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Lifestyle">Lifestyle</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Real+Estate">Real Estate</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Insurance">Insurance</a></td></tr>
<tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Business">Business</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Legal+Help">Legal Help</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Personal+Finance">Personal Finance</a></td></tr>
<tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Computers">Computers</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Health+Care">Health Care</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Shopping">Shopping</a></td></tr>
</table></center><div class='bottom_form'><form action="index.php" name="searchform" id="searchform" class="searchForm"><table border="0" cellpadding="0" cellspacing="0"><tr valign="top"><td class="logo"><a href="http://www.centurylink.com"><img src="./img/logo_top_home.png" alt="logo" style="visibility:hidden;"/></a></td><td class="centerCell"><div id="search_box_left_image"><img src="./img/search_box_background_left.jpg"/></div></td><td class="centerCell"><div class="inputHolder"><input type="text" size="40" id="queryBoxBottom" class="queryBox" name="search" value="list "/></div><div id="suggestionBox" style="display: none;height: 1px;"><table cellpadding="0" cellspacing="0" border="0"><tr valign="top"><td id="suggestionBoxLeft" style="height: 1px;">&nbsp;</td><td id="suggestionBoxText" style="height: 1px;"></td><td id="suggestionBoxRight" onmousedown="drag('suggestionBox',event)" style="height: 1px;">&nbsp;</td></tr></table></div></td><td class="centerCell"><input type="submit" name="submit" value="Web Search" class="button" size="50px" id="buttonsearchform" style=""/></td><td class="centerCell"><span id="buttonRightsearchform" style="margin-left:0em;"><img src="./img/search_box_button_right.jpg" class="button_right"/></span></td></tr></table></form><div id="top"></div></div>    <div id="mc_footer">
        <div class="lower_menu">
            <span id="copyright">
                &copy; 2009 CenturyLink, Inc.
            </span>
            <a href="faq.php" title="More Details">Why am I here?</a>
            <a class="last" href="prefs.php">Opt Out of this Service</a>
        </div>
    </div></body></html>root@leighton-laptop:/home/rogue#

---

### Post by zvacet on 2010-01-09
Delete **/etc/apt/sources-list.d/winehq.list** and add wine repository following [this]("http://www.winehq.org/download/deb") instructions.

---

