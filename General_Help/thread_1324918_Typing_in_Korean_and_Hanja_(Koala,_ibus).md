---
title: "Typing in Korean and Hanja (Koala, ibus)"
date: 2009-11-13
forum: General Help
---

### Post by moon2js on 2009-11-13
I just boot up a live usb with the new Koala. I went to language settings and installed an input method for Korean. I just pointed and clicked.

And it worked. I can type in hangeul/hangul with no problem. Something called ibus was involved, which I don't remember seeing before. It's probably the easiest it's ever been to jump into typing Korean from an English install of Ubuntu I've ever witnessed. Congrats.

But I can't seem to get hanja (kanji, Chinese characters) to work. In the previous version of Ubuntu with SCIM, I managed to set up both hangeul (Korean script) and hanja (kanji/ideographs) and it worked pretty much like it does on Windows or Macs, in America or Korea. The hotkeys to switch back and forth were annoying, but the Ubuntu/SCIM setup with hanja was awesome because not only did it pulldown a list of characters when you typed in the phoentic hangeul, it actually pulled up a tiny Korean hanja dictionary. So I could look through the characters and see the meaning in hangeul/Korean.

So I've got three questions.

ONE. Anyone else figure out how to get that awesome hanja dictionary popup to work in Koala? Or get hanja to work at all with the new ibus?

TWO. Anyone have any ideas for the least annoying way to switch between Korean and English. I'm interested in how other people choose to set that up. Personally, I want something as similar to a Korean or American international Windows XP setup -- the former has its owns key on the keyboard, the latter is right alt+shift (I think). I use Korean a lot on XP machines and it would be annoying if I had to do different shortcuts on every machine.

Actually, I've always wanted to just use that dumb menu meta key. All it does is act like a right click, no? Do I need that at all? Is there any problem with turning that into a &#54620;&#50689; (han/yeong, Korean/English) &#54620;&#51088; (hanja/kanji/ideograph) like an actual Korean keyboard? How would I do that? Is there any better way?

THREE. Any other thoughts on making Korean work better on an English Ubuntu? (Actually, how is it different from a Korean Ubuntu install? Don't they have to figure out how to install hangeul, hanja, and input method switch keys as well?)

Anyway, I'd like to open this thread up to general discussion. I really hope Korean inputing gets better and better on Ubuntu.

---

### Post by Irihapeti on 2009-11-14
My guess, and it's only a guess, is that previously you had scim-hangul installed. At the moment, you are using only the tables that came installed with iBus and they haven't got the same functions.

If I'm right, then you need to install ibus-hangul. It's in the repositories.

You can turn your menu key into something else if you want. Selection System -> preferences -> keyboard and then click on the layouts tab. You'll see a "layouts options" button. Click on this and then you can configure your menu key to do something more useful for you. (That's where it is in Hardy; it might be slightly different in Karmic, and I'm not in that right at the moment, so I can't check.)

I once tried a full Chinese install in an older Ubuntu, and it pulled in fonts, scim-pinyin, language files etc. I imagine a Korean version would do something similar. If you want to try that, it would be in System -> Administration -> Language Support. You may even be able to have separate Korean and English login sessions - I've not looked at that.

I ought to say that I don't know any Korean. I have been learning some Mandarin and I've found out quite a bit about input methods in the process.

I hope this is of some help.

---

### Post by moon2js on 2009-11-17
Yeah, I do have ibus-hangul installed. That was installed when I enabled Korean language support (point and clicking). I can type the Korean letters (native phonetic script called hanguel or hangul) just fine. I can't type Korean hanja (kanji/hanzi/Chinese characters) though.

On this Jaunty machine, using scim-hangul, I can type a Korean syllable and then pull up a hanja dictionary (with meanings!) and choose which character I want. That's how you input hanja (Chinese characters) in Korean (and I think the process is rather similar in Japanese. (&#54620; = &#38867;, &#28450;, &#23506;, &#38480;, &#38289;, etc.)

With ibus, I haven't figured out how to do that yet.

I checked out the keyboard layout options, but I'm a bit puzzled why it limits you to very specific changes. Essentially what I want to do is assign the right-alt key as a one-press language input switcher, and turn the menu key into the alt key that has just been displaced. But that's not one of the options. And I'm so confused by the key names -- meta, alt, super, hyper!

But I figured out how to configure ibus to switch languages with just a press of the right alt -- just what I want. I'm waiting to see if this conflicts with anything though.

oh, man the Korean font Ubuntu is using is so ugly it's almost unreadable!

If any other Korean inputters have any input on the subject, that would be welcome. How are others doing this? Maybe I can compile some guidance so this process isn't so trial and error for future Korean typers.

---

### Post by Irihapeti on 2009-11-17
You are right - the same sort of lookup system applies to Japanese kanji. Unfortunately, I know very little about iBus yet because it's so new.

There is also a ppa for iBus which might have more capabilities than the standard install version.

Re fonts: have a look at what's available through Synaptic. There are other fonts that aren't installed by default and might look nicer.

Also, there is [http://www.unifont.org/fontguide/](http://www.unifont.org/fontguide/) which might be helpful.

---

### Post by Zeniff on 2010-01-13
Hi~
I completely understand you!!! O_O

I've been pretty frustrated trying just to get basic language things to work in Linux too.

However, I feel I have some answers (which all took a long while to figure out).

Ugly Korean fonts:
I don't know what happened or changed since Jaunty, but I found that changing a couple places really helped. (I changed mine to the DejaVu fonts.)
Ubuntu's system fonts:
  System > Preferences > Appearance) 
Firefox's default Korean fonts:
  Edit > Preferences > Content > Fonts & Colors > Advanced > Fonts for: (select Korean) 
  (I couldn't seem to change the Proportional fonts part for Firefox, though.)

How I got my keyboard to act like a Korean one in both Scim and IBus:
(just like Irihapeti said, and seems to be the same in Karmic 9.10):
Go to System > Preferences > Keyboard (gnome-keyboard-properties) and from there go to the Layouts tab.
Choose the Add button add a Korean layout.
Note: Don't need to change keyboard model at all, unless it's wrong.

For mine, when I use the Korean layout with either Scim or IBus turned on, this makes the right Alt and right Ctrl keys to be like a real Korean keyboard and switch Eng/Kor and convert to Hanja. Otherwise, F9 will also convert to Hanja, at least in IBus. (Actually, IBus seems to switch on and off with Alt in my US layout too, but right Ctrl only works with the Korean layout on).

Note: I think on Windows XP, maybe you can highlight any syllable and press right Ctrl to convert. Is that right? Anyway, but in Scim and IBus, you can only convert what you have just typed. That means, the right Ctrl key (or F9) must be the very next key pressed in order to convert. Otherwise, you'll have to backspace, re-type, and then make sure to convert it. Scim's Hanja-mode is a very useful exception.

If you also want to use more layouts (maybe for Dvorak or Japanese?), you might also:
Click the Layout Options button. Yes, I agree it has a lot of very specific and confusing options and lacks any user-definable stuff. =_= ;;;
For mine, I made Alt+CapsLock change the layout and made the ScrollLock key light up to show I was using the Korean layout.
I also re-enabled the Ctrl+Alt+Backspace to kill the X server which they disabled in Karmic, because it seemed pretty useful for me when my window manager crashed leaving me without anything to click on.

Hanja dictionary:
Do you mean the one-or-two-word meanings on the Hanja list? That seems to be the same for me in Scim and IBus. If Scim has something more, please let me know! O_O Oh, I do know Scim has a Hanja-mode, where you just keep typing and it automatically converts.

You can also try Nabi, but I don't really know how to get it working consistently and forgot what features it has... Or, just re-install Scim... I keep all 3, since I don't know which will eventually win yet.......plus, Scim can type special characters! &#9734;&#9825;&#9836;&#9734;&#9825;&#9836;&#9734;&#9825;&#9836;&#9734;&#9825;&#9836;&#9734;&#9825;&#9836;&#9734;&#9825;&#9836;

If you want to switch between Scim and IBus or if IBus doesn't turn on by default, you can change it in System > Administration > Language Support.
  

Overall, I still have problems too, though. I still don't know why the default Korean fonts became very poor in Karmic. I also can't even find out how to conveniently type punctuation in the Chewing Chinese IM...
 
With all the trouble just to find what should be basic information, I've kind of come to the conclusion that if there is much out there, at least not in English. It's probably mostly or only written in the language that we're trying to get working... which can be hard for beginners to another language. :(
 
Also, I'm disappointed because as far as I can tell, IBus cannot yet enter special, non-Hanja characters. In Scim (just like on Windows XP's IME, not sure Mac), I can enter many different special characters by entering any Korean consonant (pretty much most of the left side of the keyboard) and then pressing the Hanja key to get things like these:
  &#9734;&#9825;&#9836;
 
Anyway, gee.... sorry for the long post... ^^;;;

By the way, Irihapeti, Hi and thanks again for making the Chewing Chinese IM package for Puppy Linux!!! It works! ^^/

Hope something in all of that text-mess helps~

---

### Post by jodonald on 2010-09-28
> **moon2js said:**
> TWO. Anyone have any ideas for the least annoying way to switch between Korean and English. I'm interested in how other people choose to set that up. Personally, I want something as similar to a Korean or American international Windows XP setup -- the former has its owns key on the keyboard, the latter is right alt+shift (I think). I use Korean a lot on XP machines and it would be annoying if I had to do different shortcuts on every machine.

This is what i used, quite simple and i can switch between keyboard by simply using ctrl+space.


> **praveenkovvuri said:**
> [SIZE=5]Follow the following steps.U may get it[/SIZE]


I found a [post in ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1498411") that explained how to enable Korean input.
 1. Enable Korean language support by going to System>  Administration> Language Support. Click on Install / Remove  Languages, select Korean from the list and Apply Changes. Select scim as  the Keyboard input method system.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean1.png?w=700&h=268[/IMG]
 2. Go to Applications> Ubuntu Software Center and search for scim-hangul and install Hangul Input Method Engine for SCIM.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean2.png?w=700&h=154[/IMG]
 3. On my computer [SCIM]("http://www.scim-im.org/") was  installed by default, but if not you can install it in the Ubuntu  Software Center. It is called SCIM Input Method Setup. After it is  installed you can find it under System> Preferences> SCIM Input  Method Setup.
 4. Restart your computer.
 5. Activate SCIM by inputting ctrl + space bar. You should see a  floating menu on the bottom right corner and/or a keyboard icon in the  upper right corner. Both allow you to switch between Korean and English.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean3.png?w=334&h=122[/IMG]
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean4.png?w=233&h=118[/IMG]
 My preferred font for reading Korean text is Baekmuk Dotum and  Baekmuk Gulim which are nicely legible. These can be installed through  the Ubuntu Software Center by searching for Baekmuk series TrueType  fonts. Then in Firefox, you can enable them by going to Edit>  Preferences. Select the Content tab and select Advanced and then you can  choose the fonts for Korean.
 [IMG]http://newtoubuntu.files.wordpress.com/2010/07/korean5.png?w=700&h=526[/IMG]

---

