---
title: "chinese input in openoffice.org"
date: 2006-01-28
forum: General Help
---

### Post by polt on 2006-01-28
can someone tell me how to activate chinese input in openoffice.org?  i followed the chinese input HOWTO and got the SCIM thing downloaded.  i can type chinese characters in firefox, and text editors and everything.  i just don't know how to do it in openoffice.  is it possible?  i chose the correct foreign language fonts in openoffice settings, but it doesn't have anything that allows me to swiitch to typing in chinese, or else i don't know where to find it.

---

### Post by ephman on 2006-03-09
is openoffice just crashing?  that's what happens to me.  and i've installed everything.

thanks,
ephman

---

### Post by polt on 2006-03-13
[QUOTE=ephman]is openoffice just crashing?  that's what happens to me.  and i've installed everything.[/QUOTE]

i've had it crash when i tried to past characters in from the text editor.  usually it is just nonresponsive though.  i couldn't figure out how to work it, so i just use abiword for chinese input instead.

---

### Post by muzaki on 2006-03-13
the program is ok... i think...
for  a while ago i got the same thing...
i want to ask you, have u done these :
1.  System>> Administration>>Language Selector
 click on translation and language aid  of the language u need
2. goto synaptic>>search>>chinese>>enter
 it will show u bunch of package u need for chinese input
3. i use automatix for upgrading open office, did u?

---

### Post by shanghaielaine on 2006-09-25
hey, polt,
I have the same problem as you did... scim works in my kubuntu everywhere excpt in OOwriter. did you so far fix it, and how?
thanks.

---

### Post by Abiezer on 2006-10-19
Not sure if this helps, as it seems too simple, but I find entering Chinese into OOWriter using SCIM no problem under Gnome. 
Once the document is open, I just hit the keyboard shortcut (CTRL-Space for me) to bring up the pinyin entry method I use and get typing. No need to select a font or anything. Is it just a case of finding the right key switch for SCIM?

---

### Post by tramax on 2006-11-10
Have the same problem ! Skim is working on every QT application (KDE style) like kate, kwrite, etc. while it is not working under Openoffice.org writer (OOwriter). 

I can add: 
- if running ooffice --writer from a terminal I can see that when I try to invoce the ime (CTRL+space), errors are reports to stdout;
- Openoffice.org writer + skim used to work with Dapper (I've just upgraded to Edgy).

Anyone managed to have this duo working ??

thx,
Trx

---

### Post by Ytse on 2006-12-06
It works well everywhere except Openoffice :(

---

### Post by Ytse on 2006-12-07
OK!!  It now works, here's what i did.  Install native japanese support, maybe this is not the cause of working, but now i have a complete japanese desktop that someday i'll completly understand.  Install im-switch and select "scim" as default. Now ctrl+space works, even in openoffice :)

I noticed the changes after reboot, dunno if it is necessary.

---

### Post by tramax on 2006-12-15
As indicated by muzaki I added the proper language using the language selector utility: this way the command *locale -a* now shows the locale I need ( zh_CN.UTF-8 ). Moreover, as I do not want to have chinese affecting all the system, didn't change my locale but did as follows. To run QT (native KDE gui) compliant applications, open a terminal (wrote a script actually) and issue *QT_IM_MODULE=scim kwrite* for example ... Scim is automatically started, so is kwrite then, when you close the editor, scim is terminated !! This doesn't work with OpenOffice.org (don't know why) so I issue *scim -d LC_CTYPE=zh_CN.UTF-8 oowriter*. I've noticed that when I use OpenOffice.org writer this way, it tends to crush: didn't undertand if TT fonts I use (supporting chinese character set, like "AR PL xx BIG5 | GB2312" ) are involved or this is an oowriter bug (at console I receive some Gtk-CRITICAL errors with references to gtype.c ??).

Thx, tRX

---

### Post by mhenriday on 2006-12-17
My **SCIM** settings (default) for the command that is to activate Chinese or Japanese text is the following : 'Control+space,Shift+space,Zenkaku_Hankaku,Hangul.' I have not been able to get **SCIM** to work anywhere on my computer, on which **Ubuntu 6.10** is presently installed, neither in Gmail or OOo. Can it be that I suffer from a plethora of activating commands, and that I should choose only one of them, say 'Control+space', for Chinese, and another, say, 'Shift+space', for Japanese ? As it is now, when I attempt to use these keyboard commands and then type a Chinese or Japanese phrase in an OOo using the letter keys on my keyboard, the only thing I get is a wavy red line under the letter string, informing me that the string does not constitute a word in my default language - a message for which, of course, I am extremely grateful. As I am new to **Ubuntu** and dependent on being able to write strings like &#12298;&#22825;&#28436;&#23398;&#21021;&#31062;&#8213; &#36798;&#23572;&#25991;&#36716;&#12299; for the research I am doing, I'd be most happy for any help I can get....

Henri

---

### Post by mhenriday on 2006-12-18
> **Ytse said:**
> OK!!  It now works, here's what i did.  Install native japanese support, maybe this is not the cause of working, but now i have a complete japanese desktop that someday i'll completly understand.  Install im-switch and select "scim" as default. Now ctrl+space works, even in openoffice :)

I noticed the changes after reboot, dunno if it is necessary.

Leaving aside the question of installing a Japanese desktop, _what_ is that 'im-switch' you installed, _where_ did you find it and _how_ and _to what_ (where) did you install it ? Do you have access to both Japanese and Chinese input ? I'm really quite concerned to get get my Chinese and Japanese input mechanisms working (unlike many of you, I have not been able to input these languages anywhere in **Ubuntu**) ; I suspect that the problem lies in that I don't know how to properly configure **SCIM**. Would anyone be willing to walk me through the procedure (remember, I need access to _both_ Chinese and Japanese), or at least point me to a source that does ?...

Thanks in advance !

Henri

---

### Post by seshomaru samma on 2007-01-18
mhenriday
read[ this ]("https://help.ubuntu.com/community/SCIM")

---

### Post by mhenriday on 2007-01-20
> **seshomaru samma said:**
> ...
read[ this ]("https://help.ubuntu.com/community/SCIM")

**Seshomaru samma**, &#26377;&#38627;&#12358; !&#12288;

My problem was that I lacked the line «/SupportedUnicodeLocales = sv_SE.UTF-8» in my ~/.scim/global file. Now **SCIM** seems to be working quite well....

&#32769;&#26429;
&#25140;&#23433;&#29702;

&#38931;&#39318;

---

### Post by emry on 2007-02-04
I followed the howto in order to get Japanese working with OOo, with the following results.

If I load into a Japanese language environment, scim anthy works perfectly.  If I load into an English language environment, it doesn't work at all in OOo.
:/

---

### Post by sarc on 2007-02-04
Me friend uses a PenPower graphic tablet to input into windows and will not touch Ubuntu until the tablet works (it won't as Penpower emailed me 'they will not develop Linux drivers' ).  Don't know if Wacom has Chinese software.  If anyone knows how to input characters using a stylus pls let me know!

---

