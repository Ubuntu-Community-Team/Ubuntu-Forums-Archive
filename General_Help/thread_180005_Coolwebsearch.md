---
title: "Coolwebsearch?"
date: 2006-05-21
forum: General Help
---

### Post by rich.bradshaw on 2006-05-21
In Windows I had this really useful toolbar in the internet thing called something like coolwebsearch. It had this toolbar that had a box to search the web and other useful things. Is there anyway to get this working on Linux? I don't think I ever downloaded it specially, it just appeared one day - does anyone know the website to download it?

I have heard of Wine, perhaps this might help me?

---

### Post by dmizer on 2006-05-21
cool web search is malware.  it is not a good thing to have on your system as it loads software onto your computer without asking.

very very bad stuff, if you're using it on windows, you'll need a special tool to remove it called cwshredder.

edit to add:
just in case you think i'm pulling your leg ... [http://www.spywareguide.com/product_show.php?id=599](http://www.spywareguide.com/product_show.php?id=599)

---

### Post by Sef on 2006-05-21
You don't want that on your computer.  Here is what Spywareguide says about it.

[http://www.spywareguide.com/product_show.php?id=599]("http://www.spywareguide.com/product_show.php?id=599")

> Full Name:
	CoolWebSearch Websearch
Type: 	Adware
Also Known as: 	CWS CoolSearcher Cool Web Search BootConf MSInfo SvcHost DNSRelay DataNotary Trojan.Norio Jetseeker winlink XPlugin coolwwwsearch Aze Search Toolbar Trojan.StartPage (Sunbelt) WinRes Spyware.CHM.A ieak6.CWS CoolWebSearch.info
SG Index: 	10 [Explain]
Removal tools: 	List of products that detect/remove/protect against CoolWebSearch:
# X-Cleaner
# RTGuardian
# Greynet Enterprise Manager
Category Description: 	Program that delivers advertisments on your PC.

Note that many websites have their own advertising, unrelated to adware.

Adware is any software application in which advertising is displayed while the program is running. The authors of these applications include additional code that delivers the ads, which can be viewed through pop-up windows or through a bar that appears on a computer screen and sometimes through text links or in integrated search results. Adware may or may not track personal information. It may also gather information anonymously or in aggregate only. Users should check the EULA and Privacy policy to ensure if the adware on their machines conforms to their standards.
Official Description: 	One of the most infamous highjackers known to date. Comes in a variety of versions, all using different techniques.

Handle with extreme care!

CoolWebSearch is a name given to a wide range of different browser hijackers. Though the code is very different between variants, they are all used to redirect users to coolwebsearch.com and other sites affiliated with its operators.
Comment: 	Known variants:

CoolWebSearch/DataNotary: earliest known variant, hijacking to datanotary.com. Drops a CSS stylesheet file in the Windows folder and sets it to be used as the user stylesheet for all web pages viewed in IE. The stylesheet includes embedded JavaScript code which tries to guess when the user is viewing porn sites.

CoolWebSearch/BootConf: drops a user CSS file in the same way as DataNotary, but pointing at [www.coolwebsearch.com](www.coolwebsearch.com). Also hijacks the home page and all search settings to point to coolwebsearch, and hacks the DNS Hosts file to redirect access of MSN address-bar search to coolwebsearch.com. The site names are obfuscated using URL-encoding (%XX) to make them difficult to read. A program bootconf.exe is set up to run on every startup, resetting the hijack. Finally coolwebsearch.com is added to the Trusted Sites list, along with msn.com, whom coolwebsearch are also impersonating.

CoolWebSearch/MSInfo: another user-CSS-hijacker, this time pointed at true-counter.com, currently redirecting to global-finder.com.

CoolWebSearch/SvcHost: a Hosts file hijacker, which works in a rather unusual way (probably to avoid being detected by anti-hijacker tools). Its targeted sites (Yahoo Search, MSN Search and all countries’ versions of Google) are set in the Hosts file to point to ‘localhost’ (127.0.0.1). Since the local host (the computer the browser is running on) is most often not running a web server, this results in an error page; it is this error page that is then hijacked to the CWS site slawsearch.com.

CoolWebSearch/PnP: a search hijacker that hides inside the ‘inf’ folder usually used for storing device driver information. Its hijacker file oemsyspnp.inf is run on each startup, using a slightly different install command each time. This command cycles through install sections 'RunOnce', 'AudioPnP', 'VideoPnp', 'IdePnP' and 'SysPnP', though quite why is unknown as it does the same thing regardless of which section is used, namely hijacking home page and search settings to point at [www.adulthyperlinks.com](www.adulthyperlinks.com) and [www.allhyperlinks.com](www.allhyperlinks.com). It also adds activexupdate.com to the IE ‘Safe Sites’ list, for unknown purpose (this is not the same as the Trusted Sites Zone).

CoolWebSearch/MSSPI: a search results hijacker implemented as a Winsock2 Layered Service Provider (a fairly low-level networking component, which is tricky to remove). Targets Google, Yahoo and Altavista, opening advertising from unipages.cc.

CoolWebSearch/DNSRelay: an address bar search hijacker implemented as an IE URL Search Hook. As well as search phrases, entering any site name into the address bar without a leading ‘[http://’](http://’) or ‘www’ will result in a search aimed at activexupdate.com, a CWS site redirecting through yellow2.com to allhyperlinks.com.

CoolWebSearch/Winres: It registers Winres.dll under %Windir%. Then it changes the Start Page to about-blank.(This page itself looks like a Search engine). It changes the start page frequently.It downloads and installs other adwares like 2020 search, isearch.. Etc., It adds some of the sites into trusted zone. It also creates two shortcuts on Desktop.
  	 
Manual removal: 	Removal can be extremely complex, and is dependant on the version. We strongly advise you do not try manual removal but use an anti-spyware tool.

# Properties: 	 Attacks security software
#  Stealth Tactics
#  Adds other software
#  Changes browser
#  Stays Resident
#  Overwrites Affiliate tracking
#  Connects to the internet
#  Shows ads

---

### Post by dmizer on 2006-05-21
heh Sef, you're too slow ... point 1 -> dmizer ;)

also noted that you indicated that you don't remember loading it onto your computer.  it did so without asking you.

want to know why internet is so slow in windows?  why you're getting so many popups? ... coolwebsearch is why.

---

### Post by rich.bradshaw on 2006-05-21
Sorry... I was just being an idiot.

Has anyone ever tried to run things like this under wine? Has anyone ever compiled and run a virus to see what would happen? 

The first time I installed WinXp under Vmplayer, I didn't install any antivirus or upgrade to SP2, as I didn't really think about it. After a few hours the virtual machine basically died, and installing AVG revealed that my virtual machine had 4 viruses. Can this happen in Wine? Surely viruses could edit files in ~/.wine/drive_c/system the same as they would in a real windows installation?

---

### Post by dmizer on 2006-05-22
[QUOTE=rich.bradshaw]The first time I installed WinXp under Vmplayer, I didn't install any antivirus or upgrade to SP2, as I didn't really think about it. After a few hours the virtual machine basically died, and installing AVG revealed that my virtual machine had 4 viruses. Can this happen in Wine? Surely viruses could edit files in ~/.wine/drive_c/system the same as they would in a real windows installation?[/QUOTE]
i remember seeing this a while back but i had difficulty hunting it down again.  here's about viri in wine: [http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

