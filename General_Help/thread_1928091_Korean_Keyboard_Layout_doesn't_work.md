---
title: "Korean Keyboard Layout doesn't work"
date: 2012-02-19
forum: General Help
---

### Post by eljc2 on 2012-02-19
I recently installed Ubuntu 10.04 on my flat mate's laptop. She is from South Korea. Hey laptop keyboard has the usual qwerty keys plus each key also has a Korean symbol.

How can I set up Ubuntu so that she can toggle between the qwerty and Korean keyboard layouts?

Here is what I have tried

System > Administration > Language Support > Language Tab > Install / Remove Languages... > Select Korean

System > Preferences > Keyboard > Layouts > Add... > add 'Korea, Republic of layout' and 'Korea, 101/104 Key Compatible'

This allows the user to toggle between 'GBr' and 'USA' keyboard layouts and the two Korean layouts. However, when any of the Korean layouts are selected and keys are pressed, the roman characters appear and not the Korean ones.

Can anyone help? It would be a shame to lose a new Ubuntu user due to this issue.

---

### Post by oklokl on 2012-02-19
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212965&d=1329671220[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212967&d=1329671358[/IMG]


sudo apt-get update && sudo apt-get install nabi

sudo -i im-switch -c
2 number

rebooting

---

### Post by eljc2 on 2012-02-19
Sorry I cannot read Korean, so I don't understand the images you pasted.

The nabi package was installed already.

I tried typing sudo -i im-switch -c and got the text below. What should I do from here?


No system wide default defined just for locale en_IE .
Use "all_ALL" quasi-locale and set IM.
System wide default for all_ALL locale is marked with [+].
There are 3 choices for the alternative xinput-all_ALL (providing /etc/X11/xinit/xinput.d/all_ALL).

  Selection    Path                                 Priority   Status
------------------------------------------------------------
* 0            /etc/X11/xinit/xinput.d/default       10        auto mode
  1            /etc/X11/xinit/xinput.d/default       10        manual mode
  2            /etc/X11/xinit/xinput.d/default-xim   0         manual mode
  3            /etc/X11/xinit/xinput.d/none          0         manual mode

Press enter to keep the current choice
[*], or type selection number:

---

