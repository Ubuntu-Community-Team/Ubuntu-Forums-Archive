---
title: "Help with program installation."
date: 2010-05-16
forum: General Help
---

### Post by s_maqbool on 2010-05-16
Hello everyone,

I'm fairly new to using ubuntu, i've had in on my netbook for a few months now as my older brother said it would work better, which it does. Though I don't know the first thing about ubuntu.

I've been trying to install a program called Zekr which is a islamic program that recites the quran. It installs through the software package manager fine and when I try it open it I get an error message which says;-

"Uthman-taha experimental theme cannot be used. Install tff-me-quran to enable uthman-taha theme."

When I try and install tff-me-quran with the instructions on the zekr website it won't find the file.

Is there any other way to get this program to work?

Any help would be appreciated.

Kind Regards,
Shaz

---

### Post by eltonw on 2010-05-16
> **s_maqbool said:**
> Hello everyone,

I'm fairly new to using ubuntu, i've had in on my netbook for a few months now as my older brother said it would work better, which it does. Though [COLOR="Red"]I don't know the first thing about ubuntu.[/COLOR]

I've been trying to install a program called Zekr which is a islamic program that recites the quran. It installs through the software package manager fine and when I try it open it I get an error message which says;-

"Uthman-taha experimental theme cannot be used. Install tff-me-quran to enable uthman-taha theme."

When I try and install tff-me-quran with the instructions on the zekr website it won't find the file.

Is there any other way to get this program to work?

Any help would be appreciated.

Kind Regards,
Shaz

First of all, [COLOR="DarkRed"]which *RELEASE* of Ubuntu are you using[/COLOR]? 

I'm using Lucid Lynx 10.4. You also did not say how you are trying to install the application. If from a console prompt [in windows this called a "command line"], you would open a terminal and do: "sudo apt-get install Zekr" , (*without the quotes*, of course). 
After providing your root password, **apt** would **_get[_/B] and [B]_install_** the application including _needed dependencies ... in this case uthman-taha theme_ (instead of u-t 'experimental'.

For the novice (newbie) like you it would be easier to use **synaptic** (it's in the admin section of ubuntu: "Synaptic Package Manager"), ***or*** the Ubuntu Software Center. Looking in the latter _as I type this reply_, I *do indeed* find **Zekr** listed among the available packages. I would simply click on "Install" and supply my superuser password. 

[FONT="Comic Sans MS"][SIZE="2"][CENTER](It's *that* easy!)[/CENTER][/SIZE][/FONT]\\:D/

Permit me to point you:arrow: to **[COLOR="Red"]some useful links for a newcomer[/COLOR]** to **GNU/LINUX**:

[http://www.linuxnewbieguide.org/]("http://www.linuxnewbieguide.org/")

[http://sites.google.com/site/easylinuxtipsproject/]("http://sites.google.com/site/easylinuxtipsproject/")

[http://www.linux.ie/newusers/beginners-linux-guide/]("http://www.linux.ie/newusers/beginners-linux-guide/")

[http://www.linuxlots.com/~jam/]("http://www.linuxlots.com/~jam/")

[http://linuxsurvival.com/]("http://linuxsurvival.com/")

I trust the above will prove invaluable to you in furthering your knowledge and use of this OS!8)

respectfully...

---

### Post by s_maqbool on 2010-05-18
I'm using the new Ubuntu LTS 10.4 version, i think it was. I've been trying to install Zekr by the synaptic package manager on my netbook.

It installs the program but won't open, giving me the error message above.

Thanks for the links aswell, will take a look at them.

---

### Post by maybeway36 on 2010-05-18
That sounds to me like a bug in Ubuntu's package of Zekr that should be reported on Launchpad.

---

### Post by s_maqbool on 2010-05-20
I have no idea how to do that, could you tell me how to do it?

---

### Post by dewapur on 2010-05-25
Actually without using uthman-taha heme, zekr still able to work normally. I just installed zekr and added new translation. It works just fine. Now i'm adding(downloading) offline recitation. For more info about zekr, you can access to [http://zekr.org](http://zekr.org)

I'm using Ubuntu Lucid

---

### Post by iqbal.shirol on 2010-08-23
Hey Everybody..

I have installed zekr successfully, and also able to open it. But the recitation does not play. The first day of the installation it played the audio without the extra fonts installed. Then I installed the required fonts after downloading them, by typing the following in the terminal:

```
sudo dpkg -i ttf-me-quran_1.003+4_all.deb ttf-sil-scheherazade_1.001-0_all.deb
```

Then the next day when I tried to play the recitation. Its not working. When I click the plat button nothing happens. Please help me on this..

Regards,
IQBAL

---

### Post by noobda on 2011-06-07
```
net.sf.zekr.engine.audio.PlayerException: javazoom.jlgui.basicplayer.BasicPlayerException: Gain control not supported
    at net.sf.zekr.engine.audio.DefaultPlayerController.setGain(DefaultPlayerController.java:187)
    at net.sf.zekr.engine.audio.DefaultPlayerController.setVolume(DefaultPlayerController.java:243)
    at net.sf.zekr.engine.audio.ui.AudioPlayerForm$14.mouseUp(AudioPlayerForm.java:553)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:213)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1258)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3540)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3161)
    at net.sf.zekr.ui.BaseForm.loopEver(BaseForm.java:34)
    at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:63)
    at net.sf.zekr.ZekrMain.main(ZekrMain.java:91)
Caused by: javazoom.jlgui.basicplayer.BasicPlayerException: Gain control not supported
    at javazoom.jlgui.basicplayer.BasicPlayer.setGain(Unknown Source)
    at net.sf.zekr.engine.audio.DefaultPlayerController.setGain(DefaultPlayerController.java:185)
    ... 10 more
```

when i try use this software (zekr) im getting this msg.. 
can nyone help me plz...

---

