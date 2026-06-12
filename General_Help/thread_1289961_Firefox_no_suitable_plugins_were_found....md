---
title: "Firefox no suitable plugins were found..."
date: 2009-10-13
forum: General Help
---

### Post by projectbronco on 2009-10-13
I'm trying to do some work on a real estate site, but it won't show me the whole page. It says "Install Missing Plugins" which I click on, but then when I proceed, it just says, "no suitable plugins were found." Then I try to get more info and it shows me a bunch of plugins from flash to quicktime. So, I don't even know which one I need. The source code for the website is at the end of this query. I can't really give a link because it's a password protected site...
The info for all the pictures was just that they were .gif files, then it said:Content-type            text/html;charset=iso-8859-1
If that helps at all.
I just need to know what plugins I need to make it work. I also attached a picture of my plugins.

Thanks for all the help.

<script language='javascript'>window.status = 'name  :  Sierra North Valley MLS © 1998-2009';</script>
<html>
	<head>
		<title>Paragon -- Online MLS for Real Estate Professionals</title>
		<link rel="shortcut icon" href="favicon.ico" >
		<meta http-equiv="content-type" content="text/html;charset=iso-8859-1">
	</head>

	<script language="JavaScript">
		var oLoader = new Loader();

		oLoader.addElement("Tabs");
		oLoader.addElement("frmMain");

		function Loader()
{
this.aElements  = new Array();
this.setElement = _setElement;
this.addElement = _addElement;
function _setElement(sName, fOnLoad)
{
var bLoadedAll = true;
for (var iCount = 0; iCount < this.aElements.length; iCount++)
{
if (this.aElements[iCount].sName == sName)
{
this.aElements[iCount].bLoaded = true;
this.aElements[iCount].onload  = (typeof(fOnLoad) == 'function') ? fOnLoad : this.aElements[iCount].onload;
if (!bLoadedAll) break;
}
if (!this.aElements[iCount].bLoaded)
bLoadedAll = false;
}
if (bLoadedAll)
for (var iCount = 0; iCount < this.aElements.length; iCount++)
this.aElements[iCount].onload();
}
function _addElement(sName)
{
this.aElements[this.aElements.length] = new Element(sName);
}
}function Element(sName)
{
this.sName   = sName;
this.bLoaded = false;
this.onload  = _onload;
function _onload() {}
}		
	</script>

	<frameset name="fstMain" rows="92,20,*" framespacing="0" border="0" frameborder="no">
		<frame name="Navigation" src="HomePage/Banner.aspx" scrolling="no" frameborder="no" noresize>
		<frame name="Tabs" src="Tabs.asp" scrolling="no"  frameborder="no" noresize>
	    <frame name="frmMain" src="HomePage/Default.aspx?root=1" marginheight="0" marginwidth="0" scrolling="auto">
	</frameset>
</html>

---

### Post by easoukenka on 2009-10-13
I dont see from your post what you need but I have never had luck with the firefox add on working for linux.  

Just use your package manager and look up flash, mplayer firefox.  Those are most common but you may also need java.  

You can also just type in firefox in the package manager and look through the plugins.   

I personally recommend getting the flash plugin right from adobe's site as I like to have the newest version.

---

### Post by easoukenka on 2009-10-13
posted twice?

---

### Post by projectbronco on 2009-10-13
Thanks for the response!
I used this link to upgrade to the x64 version of flash...
[http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html]("http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html")
It still didn't help, I also installed mplayer... I even restarted my computer afterwards to see if that would help, but it didn't.

At the bottom of the page when I first load it, it does say "Applets started" but then it still doesn't show the info I need, wich is just a basic column listing of info. It still says "Install missing Plugins" but then gives me the same crap about no suitable plugins...

The site was written in Javascript, could my Java affect it?

Thanks again for any help.

---

### Post by projectbronco on 2009-10-14
I went to the java website and did there test to see if java was working, and the image doesn't show up...
[http://java.com/en/download/help/testvm.xml]("http://java.com/en/download/help/testvm.xml")
I have java enabled, I have the icetea plugin...am I missing something.
I just want this site to work so I can work. lol

Also, the java website says I'm running ver. 1.4.2_02...but I thought I uninstalled the old version and installed version 6...twice. (I thought I messed up the first time).
I even have sun java6 jre and ia32 sun java6-bin in my spm.

Thanks for any help.

---

### Post by projectbronco on 2009-10-16
I checked and the acrobat reader isn't showing as working, javascript is working, flash is working, etc.
I'm working on getting acrobat reader installed, but it's not going well...
I got an error in the terminal:
Errors were encountered while processing:
 AdbeRdr9.1.2-1_i386linux_enu.deb

So I double clicked on the .deb file and the package manager opened and I got this:
Status: Error: Wrong architecture 'i386'

If it helps, I have the 64 bit ubuntu 8.10.

---

### Post by projectbronco on 2009-10-17
Any help...please...?

---

### Post by projectbronco on 2009-10-19
I totally uninstalled my adobe reader. I figured if it's not working, I now have a clean pallet to work with. 
Flash is still working, as is javascript...according to the tests that is...


I even tried opening this site on my windows 2k laptop and it won't open, but it opens on my dad's vista laptop. Is it a vista conspiracy?!?! Should I be afraid?!

---

### Post by 565Customz on 2009-10-19
im haveing same problems getting codecs. im trying a couple now, ill let you know

---

### Post by 565Customz on 2009-10-19
ok i got it...

go to the synaptic pacakge manager, and search for "flash"

check the package "flashplugin-installer"   accept the other files it marks, then click apply....

then go back to synaptic and select package "flashplugin-nonfree"  and apply..then restart firefox and you should be good to go...thats what i did and its working.

---

### Post by projectbronco on 2009-10-19
OK, I see flashplugin-nonfree, but not flashplugin-installer. Is there a way to get that...I'll search the forum.

Also thanks for the response.

---

### Post by 565Customz on 2009-10-19
in the terminal

sudo apt-get install flashplugin-installer

---

### Post by 565Customz on 2009-10-19
you might not have all the repositories open, that might be why you couldnt find it in synaptic. im using all four repositories

---

### Post by projectbronco on 2009-10-19
steve@Compy:~$ sudo apt-get install flashplugin-installer
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer


It can't find it...is this for something other than 9.04? Because I only have 8.10.

---

### Post by projectbronco on 2009-10-19
Which ones do I need to have open?
For Ubuntu software, the only one I don't have checked is "Source code"
And for Third Party I only have three checked: [http://ppa.launchpad.net/reacocard-awn/ubuntuintrepid](http://ppa.launchpad.net/reacocard-awn/ubuntuintrepid) main, Akirad Repository-Main, and Medibuntu-Ubuntu 8.10 "intrepid ibex" free non-free"

---

### Post by 565Customz on 2009-10-19
go to synaptic>setting>repositories  and put a check mark next to all the repositories under ubuntu software (main, univers, restricted, and multiverse)

then search for it again after you restart synaptic...

once you enable the other repositories, your probably going to get a message about all these files you can update...etc etc...just ignore them unless you want to install them.

---

### Post by 565Customz on 2009-10-19
ok, typed that before i read your other post...i dont know why you arent getting it. its in the repositorie, and that command i gave you works. 


try looking again in synaptic maybe your just over looking it lol.

---

### Post by 565Customz on 2009-10-19
also you can try just installing the nonfree and see if it works

sudo apt-get install flashplugin-nonfree

restart browser and see if it works.

---

### Post by projectbronco on 2009-10-19
Those have always been checked...I went ahead and reloaded it and tried the search again anyway, but it gave me the same message.


Whoops!!!Sorry, I thought you meant try the sudo apt-get install flashplugin-installer again. The plugin is working right now. Thanks. I'll see if it fixes the web site.

---

### Post by 565Customz on 2009-10-19
let me know

---

### Post by kpholmes on 2009-10-19
your running 64bit right?

head over to the 64bit threads, i think they have a sticky'd thread about installing java or flash on 64bit ubuntu with the new drivers, im not to sure but when i was testing 64bit i found a lot of good info over there aswell

---

### Post by projectbronco on 2009-10-19
Still no go...coming here was my last ditch effort. Their support on the website says they won't support Linux for 6 mo. to a year. And that you need at least Win 2k and IE. I was just hoping I could somehow beat the system. I guess not. I even tried that User Agent Switcher. I guess I just have to face facts...Linux can't do everything.
It is a sad day. lol
I really appreciate the help though.

---

### Post by 565Customz on 2009-10-19
actually linux can...download a bootleg version of ie and run it with wine...problem solved

---

### Post by projectbronco on 2009-10-20
OK, I found this thread, and am going to ry to follow it...
[http://ubuntuforums.org/showthread.php?t=1043510]("http://ubuntuforums.org/showthread.php?t=1043510")

---

### Post by 565Customz on 2009-10-20
good luck, let us know how it works out for you...thats what i love about linux. you learn as you go, and ususally you learn a bit when you mess with wine

---

### Post by JoelOl75 on 2009-10-20
As for the acrobat reader thing, since you are running x64 you need to install your deb in a terminal like:

# sudo dpkg -i --force-architecture acroreadwhatever.deb

And it'll work no prob.

---

### Post by projectbronco on 2009-10-20
565Customsz, thanks for sticking with me. Still messing with the Wine/IE, I'm going to let it take a break for the night...lol
Thanks JoelOl75 for the tip on AR, I'll try that tomarrow.

---

### Post by projectbronco on 2009-10-20
WOW!!! ie4linux works great! I had to upgrade my wine, which took a little doing, but then I got it all going and BAM! We're cookin' with propane. 
Thank you all for the help, the advise, and moral support. LOL
Seriously though, thanks. This is why I love Linux. I can come here and search, and if I can't find the answer I can ask a question. Whereas with windows, you are calling to India and they just tell you to reboot the computer...No offense India, you guys are still cool in my book.

If anyone else has my same problems...with the computer I mean, here are some links that I used.
Wine info
[http://ubuntuforums.org/showthread.php?t=871535]("http://ubuntuforums.org/showthread.php?t=871535")
Ie4Linux install walk through
[http://ubuntuforums.org/showthread.php?t=1043510]("http://ubuntuforums.org/showthread.php?t=1043510")

Also, for me at least, I had to restart my computer when I changed anything in IE (Java update, initial install, etc.) I think it thinks it's operating on windows so it want's a full on reboot...but it does work very well.

Thanks again guys!

---

### Post by 565Customz on 2009-10-20
hey man, can you explain to me again what the site had that it would allow you to use another browser? im just curious cuz this might be a issue we need to look at with the open source stuff we have.

---

### Post by projectbronco on 2009-10-20
It is a real estate site for looking at MLS listings. It just has spreadsheet like information and the like. They required a minimum of w2k, IE6, etc. I wish I could do a screenshot, but the site has sensitive information on it...
I don't exactly know what you are looking for, but if that doesn't answer your question, please let me know.

---

### Post by 565Customz on 2009-10-20
just trying to figure out  "what" about the site, wouldnt work. did you get and error message? what did it say. the more info you can give the better. also if you want to take a ss, go ahead, just use paint to black out all the pertinent info.

---

### Post by projectbronco on 2009-10-20
Initially, the it kept saying I needed additional plugins, like my original post stated. But then with your guys help, it was just the IE issue. The page attached would start to load, get to a certain point, then where the huge block of black paint is, it would keep saying loading. No matter how much I tried to reload it, restart it, etc. I tried various plugins, that one where you trick the site to think you are running IE6 on firefox didn't even work (the User Agent one). I then tried firefox on my laptop, still didn't work. Then, I tried IE on my laptop and it worked. (Oh, my laptop is a w2k machine)
Here is the screenshot:

---

### Post by 565Customz on 2009-10-21
so its some kind of applet that wouldnt load. do you know if it was java? also, did you happen to try any other programs? (like opera)

---

### Post by 565Customz on 2009-10-21
so this is what the site says. we just need to figure out what about the site isnt compatible. 

With all the different personal computing systems and web browsers on the market today, it is even more difficult for agents to know if the Paragon MLS is compatible with their system. To help you determine if your systems is in fact compatible with the Paragon MLS, we&#8217;ve provided the following short guide.

To use the Paragon MLS, your PC must have either Windows 2000, Windows XP (Service Pack 1, 2, or 3), or Windows Vista installed - these were the only operating systems that were determined to be fully compatible after extensive testing. The only two internet browsers that were determined to be compatible were Internet Explorer 6.0 and Internet Explorer 7.0.

Unfortunately, the Paragon MLS is not compatible with all operating systems and web browsers. The list of incompatible operating systems includes older versions of Windows (Windows 95 / Windows 98 / Windows ME), and any version of Mac OS. Incompatible Web Browsers include the AOL browser, the Yahoo browser, Firefox, and Safari.

Earlier this year, Microsoft released updates to its Windows XP and Windows Vista operating systems, as well as a new version of its Internet Explorer web browser. While Fidelity MLS Solutions has been unable to find any compatibility problems with the Paragon MLS and Windows XP Service Pack 3, they have not yet been able to successfully determine if any issues exist with Windows Vista Service Pack 1 or Internet Explorer 8.0 Beta.

As a result, we do not recommend that you install Windows Vista Service Pack 1 or Internet Explorer 8.0 Beta until sufficient testing has been done and an announcement has been made by Fidelity MLS Solutions. For questions or more information please contact our Systems Support Department at (925) 730-7100. Our Systems Support Department is available Monday through Friday, 7:30am to 5:30pm

---

### Post by projectbronco on 2009-10-21
I didthe java test and it shows that it is working fine...so I think cross that off. Never tried opera, don't know much about it.
Also, when called, they said that linux support might be up within 6 months to a year. Ha ha haa!

---

### Post by 565Customz on 2009-10-21
well..at least you have wine.

---

### Post by projectbronco on 2009-10-21
> **565Customz said:**
> well..at least you have wine.

Seriously! Now I can access it and do my work. Thanks again for the help.

If you think I can assist the Ubuntu community anymore with any other info about this episode, let me know.

---

### Post by 565Customz on 2009-10-21
we just need to figure out what it was trying to load, but without access to the site thats kinda hard to do. i wouldnt worry about it.

---

### Post by projectbronco on 2009-10-21
Sounds good.

---

