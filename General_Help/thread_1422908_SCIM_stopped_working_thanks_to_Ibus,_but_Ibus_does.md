---
title: "SCIM stopped working thanks to Ibus, but Ibus doesn't work either"
date: 2010-03-05
forum: General Help
---

### Post by grittyminder on 2010-03-05
Hi there,

After upgrading to Ubuntu 9.10 I suddenly was unable use SCIM to switch language input methods. After searching around, I discovered that with Ubuntu 9.10 Ibus was being used in place of SCIM. That's all fine and good, but I can't get Ibus to work. Specifically, when I open the Ibus settings pane and add my desired languages, the settings aren't saved when I exit.

So I tried switching back to SCIM. I changed my bashrc settings and set the keyboard input in language settings back to SCIM. No nice.

Honestly, I just want to be able to swich language input methods--I don't care if I use SCIM or Ibus. Can somebody lend a helping hand?

---

### Post by Intrepid Ibex on 2010-03-06
I didn't quite get your problem. Is it that you want to change your keyboard layout? This can also be done with e.g. xbindkeys or xmodmap and adding two entries for "setxkbmap -layout nameoflayout"

---

### Post by grittyminder on 2010-03-06
Ah, sorry I wasn't clear. Prior to upgrading to 9.10 I was using SCIM and everything was fine: when I pressed Ctrl+Space I was able to switch language input. After upgrading to 9.10 when I pressed Ctrl+Space nothing happened. After researching a bit, I discovered that SCIM was disabled, and in its place Ibus was enabled--this happened automatically as part of the process of upgrading to 9.10. I don't know anything about Ibus--I was perfectly happy with SCIM. 

So, I tried switching back to SCIM. In .bashrc I added

export GTK_IM_MODULE=scim
export XMODIFIERS=@im=scim
export QT_IM_MODULE=scim

because in the env "ibus" was set to the default value for the above three variables. I also set the keyboard input in language settings back to SCIM. I rebooted and checked the env and verified that the three above environment variables were set to scim. I also grepped my running processes and verified that scim was running. But again, when I pressed Ctrl+Space nothing would happen. 

Ultimately, all I really care about is that when I press Ctrl+Space I am able to switch language inputs. Right now I can't do that.

---

