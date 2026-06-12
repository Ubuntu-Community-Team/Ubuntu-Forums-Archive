---
title: "Font Problem"
date: 2010-01-04
forum: General Help
---

### Post by fparedesg on 2010-01-04
Hey UbuntuForums!

I just finished installing Office 2007 in Ubuntu 9.10 using Wine 1.2. The installation was pretty smooth, and everything works great. The only problem I have is the difference between fonts (while comparing Office using Windows and Ubuntu). Here is a screenshot of Word running in [Windows 7]("http://img526.imageshack.us/img526/4127/testcs.png"), and here is another screenshot of it running under [Ubuntu 9.10]("http://img46.imageshack.us/img46/381/test2ny.png"). (If you opened the links, make sure you're looking at the pics with 100% magnification, so that the pixels aren't distorted. :P)

In the pictures, the Arial font looks completely different, Times New Roman also looks distorted, and Calibri looks less lush under Ubuntu. Why is that?

Thanks to anyone that helps! :D As you can see, I'm pretty obsessive, so I'd like to have the fonts working fine under Ubuntu, so that I can finally switch :P

---

### Post by houseworkshy on 2010-01-04
I can't actually answer this post, though I am interested.  I write and the wp is the most important thing in a pc for me.  Assuming that you have installed Ubuntu from a standard cd then you will find that you have Open Office too.  What does the same page look like in that?  When I switched I also switched to Open office.  The transition was seamless as it could read and write from and to to all my old work, even very old Works for DOS and Word perfect.  Certainly handles more file types including exporting as pdf. It has a huge range of plugins and it's team have promised that it shall be both free and supported for good. The main reason though is that I actually prefer writing on it.

One thing you do need to do before migrating to Ubuntu, whichever wp you use, is to test your printer.  Most present no problems however some do.  Cannon are notorious for bad Linux support whilst HP are very good indeed.

Someone who knows more than me will know if there is such a thing as a restricted extras package for fonts or if one needs to do something special with cups.  The test page with open office may indicate to such a one but mostly it would just be interesting to see a three way comparison. Sorry, I'm one of those people who loose track of time browsing in Stationers.

---

### Post by hariks0 on 2010-01-04
> **fparedesg said:**
> 

I just finished installing Office 2007 in Ubuntu 9.10 using Wine 1.2.  so I'd like to have the fonts working fine under Ubuntu, so that I can finally switch :P

So this is what you mean by 'finally switching' ?:)

---

### Post by djchandler on 2010-01-04
> **fparedesg said:**
> Hey UbuntuForums!

I just finished installing Office 2007 in Ubuntu 9.10 using Wine 1.2. The installation was pretty smooth, and everything works great. The only problem I have is the difference between fonts (while comparing Office using Windows and Ubuntu). Here is a screenshot of Word running in [Windows 7]("http://img526.imageshack.us/img526/4127/testcs.png"), and here is another screenshot of it running under [Ubuntu 9.10]("http://img46.imageshack.us/img46/381/test2ny.png"). (If you opened the links, make sure you're looking at the pics with 100% magnification, so that the pixels aren't distorted. :P)

In the pictures, the Arial font looks completely different, Times New Roman also looks distorted, and Calibri looks less lush under Ubuntu. Why is that?

Thanks to anyone that helps! :D As you can see, I'm pretty obsessive, so I'd like to have the fonts working fine under Ubuntu, so that I can finally switch :P

As someone who used to typeset textbooks, I'm fairly obsessive about font appearance as well.

Have you tried adjusting your Font settings? Look in the following desktop menu.

System>Preferences>Appearance>Fonts

You can anti-alias under smoothing then adjust how type appears (hinting) on your monitor as well. As you can see there are numerous options. You should be able to adjust and make your typefaces look just as good as when using the Cleartype settings in Windows.

---

### Post by fparedesg on 2010-01-04
houseworkshy: I actually tried switching over to OpenOffice, and even though the word processor is great, I'm not very fond of the Presentation and Spreadsheet programs. I've sometimes faced problems when opening other documents someone else sends me (especially presentations), as the contents are sometimes somewhat shifted, of a different color, etc.
[EDIT] Oh yeah, the document looks fine under OpenOffice, however, as I mentioned above, I'm not really comfortable using OpenOffice, as I generally face problems with shifted paragraphs and changed colors.

hariks0: Once I get this working, I'm going to stop using Windows :P This is the only thing stopping me, actually. The only programs I need are these and a Java compiler, which is easily available in Linux.

djchandler: Thanks for your response, however, this didn't work :( This changed the system fonts, but not the fonts used in Word. The letters still look the same :\

---

### Post by djchandler on 2010-01-04
> **fparedesg said:**
> djchandler: Thanks for your response, however, this didn't work :( This changed the system fonts, but not the fonts used in Word. The letters still look the same :\

Must be that the fonts are rendered through Wine.  A big "duh" on me.

You may be able to get the ClearType Tuner PowerToy to load and run that may be able to do that, but I have no idea if it will run under Wine. It's not in [Wine's  application database.]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

[http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx](http://www.microsoft.com/windowsxp/Downloads/powertoys/Xppowertoys.mspx)

[http://download.microsoft.com/download/b/7/0/b7019730-0fa3-47a9-a159-98b80c185aad/setup.exe](http://download.microsoft.com/download/b/7/0/b7019730-0fa3-47a9-a159-98b80c185aad/setup.exe)

Have you tried running a Virtual Machine and running Office in a full Windows OS that is hosted by Ubuntu?

---

### Post by fparedesg on 2010-01-04
ClearType didn't work under Wine :(
Another thing I noticed was that changing the fonts (System - Appearance) didn't change the way the letters looked under OpenOffice either; not the document's letters, at least.

One thing I did that kind of worked (at least with the Arial Font) was this: I went into the Fonts folder in the Wine directory (/home/username/.wine/drive_c/windows/Fonts), created a backup of it, and substituted it with the Fonts folder from a Windows machine. The result is [this]("http://img707.imageshack.us/img707/4653/test3o.png"). If you compare with the older picture of Word running in Ubuntu, the Arial font looks better, but the Times New Roman and the Calibri fonts have the same ugly looking letters. xD

However, if you notice, the fonts in the top bar and menus are all scrawny looking now, I don't know why.

---

### Post by djchandler on 2010-01-04
> **fparedesg said:**
> One thing I did that kind of worked (at least with the Arial Font) was this: I went into the Fonts folder in the Wine directory (/home/username/.wine/drive_c/windows/Fonts), created a backup of it, and substituted it with the Fonts folder from a Windows machine.

That was going to be my next suggestion, although technically a violation of your Windows EULA. But let's digress a little.

First, have you checked what fonts look like in another Windows application other than an MS Office 2007 application?

Second, there are non-free items available from **[Medibuntu]("http://www.medibuntu.org/")**. We've assumed so far that you have installed the **MS Core Fonts** package from there. Have you done this? The reason there may be problems rendering fonts in **Wine** correctly may be that they are not installed in **/usr/share/fonts/truetype/msttcorefonts**. Check to see if they are there. If they aren't, install the MS Core Fonts via **Synaptic** or **apt-get**.

Here's an alternative to making fonts available for your Gnome session, but your Gnome session only. Open **Nautilus** and check the box under the **View** menu that says **Show Hidden Files**. Check for a hidden folder in your home directory called **.fonts**. If there isn't one, create it, making sure a period **(.)** precedes **fonts**. Now copy your problematic fonts into **/home/fparedesg/.fonts**. I'm assuming your user account name is fparedesg. Log out, log back in and let's see how things look now.

We may be on the right track now. Check out this [Wiki]("http://wiki.jswindle.com/index.php/Fonts").

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)

What version of Wine you are running also seems to make a difference. The Ubuntu repository is normally a bit behind the absolute latest release of Wine.

But look at this quote:
*"... if you have no fonts in the windows directory and your latest software install copies some strange and unusual font to the windows directory, suddenly all the text may look quite strange. This is easily fixed - copy the corefonts to the font directory and then wine will be able to select a better font."*

---

### Post by fparedesg on 2010-01-04
The fonts look the same in all Office applications.

I have installed the msttcorefonts and they are in /usr/share/fonts/truetype/msttcorefonts.

I tried copying all of the fonts from **/home/username/.wine/drive_c/windows/Font** to **/home/federico/.fonts**, and the Arial font seems to be different, although it is still not correctly rendered. The fonts look like [this]("http://img94.imageshack.us/img94/7506/test4p.png").

I am currently running Wine 1.1.35. I downloaded it off the WineHQ page.

---

### Post by djchandler on 2010-01-04
> **fparedesg said:**
> The fonts look the same in all Office applications.

I have installed the msttcorefonts and they are in /usr/share/fonts/truetype/msttcorefonts.

I tried copying all of the fonts from **/home/username/.wine/drive_c/windows/Font** to **/home/federico/.fonts**, and the Arial font seems to be different, although it is still not correctly rendered. The fonts look like [this]("http://img94.imageshack.us/img94/7506/test4p.png").

I am currently running Wine 1.1.35. I downloaded it off the WineHQ page.

So now you have all the fonts where Linux looks for them, but you may need to delete duplicates in your .font folder that are already in /usr/share/font/.... Then I think you need to delete all the fonts in **/home/username/.wine/drive_c/windows/Font**.

From [http://wiki.jswindle.com/index.php/Fonts#Introduction:](http://wiki.jswindle.com/index.php/Fonts#Introduction:)

[I]"Wine apparently checks the windows/fonts directory, and uses it for all the fonts in the programs it loads. If there are no fonts in this directory wine assumes that you want to use the xwindows fonts. When there are fonts in this directory wine assumes you want to use the windows/fonts fonts and not the xwindows fonts

[/I]*What this means is... if you have no fonts in the windows directory and your latest software install copies some strange and unusual font to the windows directory, suddenly all the text may look quite strange. This is easily fixed - copy the corefonts to the *(**LINUX**)* font directory *(NOT **/home/username/.wine/drive_c/windows/Font**) *and then wine will be able to select a better font" *

This is a bit confusing, huh? :confused: 

But this should force Wine to use Linux's Freetype and X to render the fonts instead of using Windows .dll libraries. Then adjusting font settings in the **Appearances** sub-menu should let you fine-tune the appearance on screen. Try emptying **/home/username/.wine/drive_c/windows/Font**.

So what happens when you print from MS Office 2007? How do your typefaces look then?

---

### Post by fparedesg on 2010-01-04
Dang, deleting the duplicates between **/usr** and **/home** might prove to be difficult, as the fonts in **/usr** are organized in folders (truetype, type1, X11). Do you think it matters if they are duplicated in those folders?

Okay, I just deleted the **/home/username/.wine/drive_c/windows/Font** folder and rebooted. The menus look fine, and the Arial font still looks somewhat bad (not as bad as how it was in the very beginning).

While printing, I noticed that the Calibri font doesn't look bad on paper. The letters are rich and full, and they look the same as the paper I printed through Windows. Times New Roman looks the same in Windows and Ubuntu. Arial looks different; Arial looks the same on paper and on the screen, all scrawny looking and thin. :(

---

### Post by djchandler on 2010-01-04
> **fparedesg said:**
> Dang, deleting the duplicates between **/usr** and **/home** might prove to be difficult, as the fonts in **/usr** are organized in folders (truetype, type1, X11). Do you think it matters if they are duplicated in those folders?

The only thing I am sure about is it will save memory. But you will have duplicates in your font table that could be confusing the issue of what font to render, and you may be getting the bitmapped X11 substitute instead of actual Arial. That's what your examples looks like to me. I remember the bad old days on Mac System 6.0.x on my black and white Mac+ when all the default Apple fonts were bit-mapped and had that stair-step appearance. That's why Adobe Type Manager and PS Type 1 fonts got so popular to use with PageMaker and other DTP applications way back then with the introduction of the Mac II series, color and grayscale graphics and therefore a method of smoothing typefaces on-screen. 

I would start by re-naming your /home/federico/.fonts to something like /home/federico/font-storage. Log out and then back in.

It would be nice to restart the X server. So re-booting may be the easiest way to do that. Alt-ctrl-backspace used to restart it in default Ubuntu installations, but that's been changed. So most people have it disabled now unless you deliberately override in your settings or restart X from a terminal window directly from the logon window without starting a Gnome session. Don't do it while in Gnome.

Anyway, when you log back in you will only be using the fonts in /usr/share/fonts/.... You should not need to worry about what is in Type 1 and X11. There should not be any duplicates there anyway. There may be shortcuts that actually point back to your truetype directory.

What does arial look like if you double-click on it and view it in Font Viewer? Do you have Font Forge installed?

Here is what Arial looks like on my laptop. Smaller sizes are definitely scrawny-looking to me too. I do not have Wine on my laptop.

---

### Post by djchandler on 2010-01-05
Federico, as you obviously have the typographer's eye, here are some interesting comparisons for you. I have Win 7 on this dual boot laptop, and it was upgraded from Vista.

My eye discerns a difference between the Vista and Win 7 versions.

Here is Arial from Vista, then from Win 7:

---

### Post by djchandler on 2010-01-05
Here is Calibri from Vista, then from Win 7

---

### Post by djchandler on 2010-01-05
Finally, here is Times New Roman from Vista, then from Win 7

---

### Post by djchandler on 2010-01-05
Okay, now I have a crazy idea. Font handling has changed so much in the last couple of releases, this had not occurred to me before. But this is essentially be the same as placing the fonts installed by Office 2007 (or that you moved from Win 7) into the **/home/federico/.fonts** directory.

Uninstall the MS Core Fonts that you installed via Synaptic. The difference between those and the Win 7 versions looks very dramatic to me. Leave the **/home/federico****/.wine/drive_c/windows/Font** directory empty.

What had not occurred to me before is that you can install fonts now through Font Viewer. But to keep it simple, just rename /font-storage back to **/home/federico/.fonts** if you did what I suggested in  #12. Copying typefaces to .fonts does exactly the same thing.

Sorry I made such a mess of this, but I just learned a lot while I was inadvertently frustrating you under the pretense of helping. I had not really looked so closely at these fonts in a while. Thanks for reminding me of the eye I have but have not been using. Please don't give up. You certainly have a discerning eye.

The newest versions of the fonts from Win 7 do look a lot better, do they not? Make sure the newest version of the MS typefaces you have access to get put into **/home/federico/.fonts**, and that will be the best available. Now go back and adjust System>Preferences>Appearance>Fonts.

---

### Post by fparedesg on 2010-01-05
Nice! I deleted the mscore fonts I had previously installed. I then deleted all of the fonts located in **/home/federico/.fonts**. I then went over to the Windows partition (I also have Windows installed in this laptop) in **/media/WINDOWS/Windows/Fonts** and double clicked and installed the fonts I used in the document in all of the screenshots (Calibri, Cambria, Arial, and Times New Roman). I noticed that said fonts were now stored in a automatically created **/home/federico/.fonts**

[This]("http://img684.imageshack.us/img684/6987/test5.png") is the newest screenshot.

If you take a look at the screenshot, the Arial font looks better. Most of the fonts look different than in the [original screenshot I took while using Windows]("http://img526.imageshack.us/img526/4127/testcs.png"), however, when I printed out a sheet while using Ubuntu, the printed paper looked exactly the same than the one I printed while using Windows.

Even though the fonts still look somewhat different (although not *drastically* different, like the way it was in the beginning), the width of both the Windows fonts and the Ubuntu fonts look the same. Before this, the fonts in Ubuntu were shorter, meaning, a complete line, while viewed under Ubuntu, would be displayed in two lines under Windows. This was a problem, [as the document's proportions weren't being correctly displayed under Ubuntu]("http://img46.imageshack.us/img46/381/test2ny.png"). This is not a problem anymore. :D

Now I just need to install the rest of the fonts (and get PowerPoint to work xP). :P

Thank you for all your help! You really, really went in-depth with this...I really appreciate it. :D

---

### Post by djchandler on 2010-01-05
> **fparedesg said:**
> Thank you for all your help! You really, really went in-depth with this...I really appreciate it. :D

It was my privilege and pleasure and you are most welcome.

We have a common interest. I totally understand the necessity of tight font control. Making sure the metrics, tracking and kerning are consistent with what you are seeing on-screen and duplicating cross-platform can be somewhat tricky. It had not occurred to me before that metrics could change that much between versions on those fonts.

Recalling what we used to do 15 years or more ago when we started using both Macs and Windows in my shop to run file compatible versions of PageMaker 5.0 was what finally steered me to the right solution. The trick then was making sure we had the exact same fonts with the exact same metrics on both. We had a handy little Mac utility called FontHopper (Ares Software, now owned by Adobe) to port cross-platform when a font was chosen for a project that happened to look a little different between the two.

Glad I could help. This is my idea of fun.

---

