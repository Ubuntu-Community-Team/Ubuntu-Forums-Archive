---
title: "Waltop Slim Tablet - Buttons don't work"
date: 2009-12-13
forum: General Help
---

### Post by maluko35 on 2009-12-13
Hi.
I have an Waltop tablet([http://www.waltop.com.tw/productDetail.asp?id=22](http://www.waltop.com.tw/productDetail.asp?id=22)), and with wizardpen driver he work fine(the pressure work perfect)  but the buttons of my pen don't work. The pen have 3 buttons, the pen tip sensitive and more 2 buttons on the body of pen.

I did the installation with this tuto: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

I tried to config the buttons with this command: xinput set-button-map "WizardPen Tablet" 1 3 2
But terminal return: unable to find device WizardPen Tablet

If i try:
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 3 2
or
xinput set-button-map "7" 1 3 2

Nothing happens, does not modify any button.:(

[SOLVED]
The problem has solved with a post of this forum([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1261407&highlight=waltop&page=117](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1261407&highlight=waltop&page=117)), i had problems with the command "make" everytime return me errors, but the problem was the spaces on the folder name.

Now, all is perfect. :)

Thanks.

---

