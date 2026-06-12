---
title: "Brother MFC-255CW"
date: 2011-05-08
forum: General Help
---

### Post by its_jon on 2011-05-08
Using the latest Unity OS.

My printer installed under Ubuntu Studio...

Now switch to the standard Ubuntu release with Unity.

When I try to download the Brother install tool it downloads as text and I have no idea how to run it.

Tried the Ubuntu Brother help thread... typing all the stuff into the terminal...

starting to pull my hair out now...

help :)

Brother MFC-255CW

---

### Post by its_jon on 2011-05-10
I logged into nautilus as root and started transferring the cups and driver files into the folders manually...drag and drop

my printer still does not appear on the list :roll:

its a Brother MFC-255CW

I have had it working .... just can't seem to work out how to get it up and running in the Unity release.

thanks
john
Scotland

---

### Post by its_jon on 2011-05-11
This was the install helper from Brother.... see code

It didd'nt download as something that ran, just as text in firefox. So... I put it into a text file.

what do I do to get it to run ?

Im sure I used this file in Ubuntu Studio and it installed the printer for me....

Do I rename it to something ?..... I dont know how to execute it (if that's the right word)

```
#! /bin/bash
#
# Copyright(c) 2010 Brother Industries, Ltd.  
#    All Rights Reserved.
#
#Brother retains any and all copyrights to the Software. 
#In no case this Agreement shall be construed to assign 
#or otherwise transfer from Brother to User any copyrights 
#or other intellectual property rights to whole or any part 
#of the Software.
#
#Brother grants User a non-exclusive license: to reproduce 
#and/or distribute (via Internet or in any other manner) the 
#Software. Further, Brother grants User a non-exclusive 
#license to modify, alter, translate or otherwise prepare 
#derivative works of the Software and to reproduce and 
#distribute (via Internet or in any other manner) such 
#modification, alteration, translation or other derivative 
#works for any purpose.
#
#The license of the Software from Brother hereunder is 
#granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH
# RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING 
#BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, 
#FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
#Brother shall have no liability in contract, tort (including 
#negligence or breach of statutory duty) or otherwise for any 
#interruption of use, loss of data, or for any indirect, 
#incidental, punitive or consequential loss or damage, or for 
#any loss of profit, revenue, data, goodwill or anticipated 
#savings that arises under, out of, or in contemplation of 
#this Agreement or otherwise arises due to any error, inaccuracy 
#or defect in the Software even if Brother has been advised of 
#the possibility of such loss or damage.
#Further, Brother shall have no liability to disclose and/or 
#distribute the source cord of the Software to User under any 
#circumstances. In no case shall the above license by Brother 
#to modify, alter, translate or otherwise prepare derivative 
#works of the Software be construed as Brother's implied 
#agreement or undertakings to disclose and/or distribute the 
#source cord of the Software.



COLOR='\033[1;31m'
COLOR2='\033[1;35m'
MONO='\033[1;0m'

if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
  MESSAGE010="USAGE:  "
  MESSAGE012="     :  "
  MESSAGE020="  model"
  MESSAGE030="   -f model"
  MESSAGE040="   -l "
  MESSAGE050="Only root can perform this operation."
  MESSAGE060="CUPS is not installed."
  MESSAGE070="Do you want to specify a PROXY server? [y/N] ->"
  MESSAGE080="Enter the URL of the PROXY server."
  MESSAGE090="   ex http://(proxy-server-url):(port)"
  MESSAGE100="   ex http://(login-name):(password)@(proxy-server-url):(port)"
  MESSAGE110="     ->"
  MESSAGE120="Unable to get the server information."\
"  Please check the network settings."
  MESSAGE121="Input model name ->"
  MESSAGE122="Rpm or dpkg is required."
  MESSAGE130="Driver-packages cannot be found."
  MESSAGE140=" Confirm the model name."
  MESSAGE150="You are going to install  following packages."
  MESSAGE160="OK? [y/N]  ->"
  MESSAGE170="Do you agree? [Y/n] ->"
  MESSAGE180="Do you agree? [Y/n] ->"
  MESSAGE182="The security level of SELinux has been temporarily lowered "\
"to enable the test print."\
"  To set it permanently, modify the SELinux configuration file."
  MESSAGE184="The security level of AppArmor has been lowered."\
"  (aa-complain cups)"
  MESSAGE190="Will you specify the Device URI? [y/N] ->"
  MESSAGE200="Specify IP address."
  MESSAGE210="select the number of destination Device URI. ->"
  MESSAGE220="  enter IP address ->"
  MESSAGE230="Test Print? [y/N] ->"
  MESSAGE240="Hit Enter/Return key."
else
MESSAGE010="ä½¿ç”¨æ–¹æ³•:  "
MESSAGE012="ã€€ã€€ã€€ã€€:  "
MESSAGE020="  ãƒ¢ãƒ‡ãƒ«å"
MESSAGE030="   -f ãƒ¢ãƒ‡ãƒ«å"
MESSAGE040="   -l "
MESSAGE050="æ¨©é™ãŒã‚ã‚Šã¾ã›ã‚“ã€‚suã‚‚ã—ãã¯sudoã‚³ãƒžãƒ³ãƒ‰ã§rootæ¨©é™ã‚’å–å¾—ã—ã¦ãã ã•ã„ã€‚"
MESSAGE060="CUPSãŒã‚¤ãƒ³ã‚¹ãƒˆãƒ¼ãƒ«ã•ã‚Œã¦ã„ã¾ã›ã‚“ã€‚"
MESSAGE070="WEBã‚ˆã‚Šæƒ…å ±ã‚’å–å¾—ã§ãã¾ã›ã‚“ã€‚PROXYã‚µãƒ¼ãƒãƒ¼ã‚’æŒ‡å®šã—ã¾ã™ã‹? [y/N] ->"
MESSAGE080="PROXYã‚µãƒ¼ãƒãƒ¼ã®URLã‚’å…¥åŠ›ã—ã¦ãã ã•ã„ã€‚"
MESSAGE090="   ä¾‹1 http://(proxy-server-url):(port)"
MESSAGE100="   ä¾‹2 http://(login-name):(pass-word)@(proxy-server-url):(port)"
MESSAGE110="     ->"
MESSAGE120="ã‚¤ãƒ³ã‚¿ãƒ¼ãƒãƒƒãƒˆã«æŽ¥ç¶šã§ãã¾ã›ã‚“ã€‚ãƒãƒƒãƒˆãƒ¯ãƒ¼ã‚¯è¨*å®šã‚’ç¢ºèªã—ã¦ãã ã•ã„ã€‚"
MESSAGE121="ãƒ¢ãƒ‡ãƒ«åã‚’å…¥åŠ›ã—ã¦ãã ã•ã„ã€‚->"
MESSAGE122="rpmã‚‚ã—ãã¯dpkgãŒå¿…è¦ã§ã™ã€‚"
MESSAGE130="è©²å½“ã™ã‚‹ãƒ‰ãƒ©ã‚¤ãƒãƒ‘ãƒƒã‚±ãƒ¼ã‚¸ãŒè¦‹ã¤ã‹ã‚Šã¾ã›ã‚“ã€‚"
MESSAGE140="ã€€ã€€ãƒ¢ãƒ‡ãƒ«åã‚’ç¢ºèªã—ã¦ãã ã•ã„ã€‚"
MESSAGE150="ä»¥ä¸‹ã®ãƒ‘ãƒƒã‚±ãƒ¼ã‚¸ãŒè¦‹ä»˜ã‹ã‚Šã¾ã—ãŸã€‚"
MESSAGE160="ã‚¤ãƒ³ã‚¹ãƒˆãƒ¼ãƒ«ã—ã¾ã™ã‹? [y/N]  ->"
MESSAGE170="ä¸Šè¨˜ä½¿ç”¨è¨±è«¾ã«åŒæ„ã—ã¾ã™ã‹? [Y/n] ->"
MESSAGE180="ä¸Šè¨˜ä½¿ç”¨è¨±è«¾ã«åŒæ„ã—ã¾ã™ã‹? [Y/n] ->"
MESSAGE182="ä¸€æ™‚çš„ã«SELinuxã®ã‚»ã‚*ãƒ¥ãƒªãƒ†ã‚£ãƒ¬ãƒ™ãƒ«ã‚’ä¸‹ã’ã¾ã—ãŸã€‚æ’ä¹…å¯¾ç*–ã¨ã—ã¦CUPSã®ã‚»ã‚*ãƒ¥ãƒªãƒ†ã‚£ãƒ¬ãƒ™ãƒ«ã‚’permissiveã«ã—ã¦ãã ã•ã„ã€‚"
MESSAGE184="AppArmorã®CUPSã«å¯¾ã™ã‚‹ã‚»ã‚*ãƒ¥ãƒªãƒ†ã‚£ãƒ¬ãƒ™ãƒ«ã‚’ä¸‹ã’ã¾ã—ãŸ (aa-complain cups)ã€‚"
MESSAGE190="Device URIã‚’æŒ‡å®šã—ã¾ã™ã‹? [y/N] ->"
MESSAGE200="IPã‚¢ãƒ‰ãƒ¬ã‚¹ã®æŒ‡å®š"
MESSAGE210="ä½¿ç”¨ã™ã‚‹Device URIã®ç•ªå·ã‚’é¸æŠžã—ã¦ãã ã•ã„ã€‚ ->"
MESSAGE220="  ã”ä½¿ç”¨ã®ãƒ—ãƒªãƒ³ã‚¿/MFCã®IPã‚¢ãƒ‰ãƒ¬ã‚¹ã‚’æŒ‡å®šã—ã¦ãã ã•ã„ã€‚->"
MESSAGE230="ãƒ†ã‚¹ãƒˆå°åˆ·ã‚’å®Ÿè¡Œã—ã¾ã™ã‹ ? [y/N] ->"
MESSAGE240="Enterã‚*ãƒ¼ã‚’æŠ¼ã—ã¦ãã ã•ã„ã€‚"
fi

if [ -e "$0".rc ];then
  source "$0".rc
fi


brother_license(){
echo -e $COLOR2
if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
cat <<BROTHERLICENSE
=========================================
Brother License Agreement

Brother retains any and all copyrights to the Software. In no case this Agreement shall be construed to assign or otherwise transfer from Brother to User any copyrights or other intellectual property rights to whole or any part of the Software.

Brother grants User a non-exclusive license: to reproduce and/or distribute (via Internet or in any other manner) the Software. Further, Brother grants User a non-exclusive license to modify, alter, translate or otherwise prepare derivative works of the Software and to reproduce and distribute (via Internet or in any other manner) such modification, alteration, translation or other derivative works for any purpose.

The license of the Software from Brother hereunder is granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
Brother shall have no liability in contract, tort (including negligence or breach of statutory duty) or otherwise for any interruption of use, loss of data, or for any indirect, incidental, punitive or consequential loss or damage, or for any loss of profit, revenue, data, goodwill or anticipated savings that arises under, out of, or in contemplation of this Agreement or otherwise arises due to any error, inaccuracy or defect in the Software even if Brother has been advised of the possibility of such loss or damage.
Further, Brother shall have no liability to disclose and/or distribute the source cord of the Software to User under any circumstances. In no case shall the above license by Brother to modify, alter, translate or otherwise prepare derivative works of the Software be construed as Brother's implied agreement or undertakings to disclose and/or distribute the source cord of the Software.
=========================================
BROTHERLICENSE
else
cat <<BROTHERLICENSEJ
=========================================
ï»¿ãƒ–ãƒ©ã‚¶ãƒ¼ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ç”¨ã€€å…¬è¡†ä½¿ç”¨è¨±è«¾å¥‘ç´„æ›¸

æœ¬å¥‘ç´„ã¯ã€æœ¬å¥‘ç´„ã¨ã¨ã‚‚ã«é…å¸ƒãƒ»æä¾›ã•ã‚Œã‚‹ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ ï¼ˆä»¥ä¸‹å˜ã«æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã¨ã„ã„ã¾ã™ï¼‰ ã«é–¢ã—ã€æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®è‘—ä½œæ¨©è€…ã§ã‚ã‚‹ãƒ–ãƒ©ã‚¶ãƒ¼å·¥æ¥*æ ªå¼ä¼šç¤¾ ï¼ˆä»¥ä¸‹ã€ãƒ–ãƒ©ã‚¶ãƒ¼ã¨ã„ã„ã¾ã™ï¼‰ ã‹ã‚‰æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢å—é ˜è€… ï¼ˆä»¥ä¸‹å˜ã«åˆ©ç”¨è€…ã¨ã„ã„ã¾ã™ï¼‰ ã«å¯¾ã—ä¸Žãˆã‚‰ã‚Œã‚‹ä½¿ç”¨è¨±è«¾ã«ã¤ã„ã¦å®šã‚ã‚‹ã‚‚ã®ã§ã™ã€‚ åˆ©ç”¨è€…ã¯ã€ä¸‹è¨˜æ¡é …ã«å¾“ã„æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã‚’åˆ©ç”¨ã™ã‚‹ã‚‚ã®ã¨ã—ã¾ã™ã€‚ ã¾ãŸã€åˆ©ç”¨è€…ã¯æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã‚’åˆ©ç”¨ã™ã‚‹ã“ã¨ã«ã‚ˆã‚Šã€ä¸‹è¨˜æ¡é …ã«åŒæ„ã—ãŸã‚‚ã®ã¨è¦‹ãªã•ã‚Œã¾ã™ã€‚

ï¼ˆï¼‘ï¼‰æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã«é–¢ã™ã‚‹è‘—ä½œæ¨©ã¯ã€ãƒ–ãƒ©ã‚¶ãƒ¼ã«å¸°å±žã—ã¾ã™ã€‚ æœ¬å¥‘ç´„ã¯ã€æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã«ã¤ã„ã¦ãƒ–ãƒ©ã‚¶ãƒ¼ã‹ã‚‰åˆ©ç”¨è€…ã«å¯¾ã—è‘—ä½œæ¨©ã®å…¨éƒ¨è‹¥ã—ãã¯ä¸€éƒ¨ã‚’è*²æ¸¡ã™ã‚‹ã‚‚ã®ã¨ã¯è§£ã•ã‚Œå¾—ã¾ã›ã‚“ã€‚ 
ï¼ˆï¼’ï¼‰ãƒ–ãƒ©ã‚¶ãƒ¼ã¯åˆ©ç”¨è€…ã«å¯¾ã—ã€æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã«ã¤ã„ã¦è¤‡è£½ã€è*²æ¸¡ ï¼ˆè‘—ä½œæ¨©ã®è*²æ¸¡ã§ã¯ãªãã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ãŒæ ¼ç´ã•ã‚ŒãŸåª’ä½“ã®è*²æ¸¡ã‚’æŒ‡ã—ã¾ã™ï¼‰ ãŠã‚ˆã³å…¬è¡†é€ä¿¡ã‚’è¡Œã†æ¨©åˆ©ã‚’ç„¡å„Ÿã«ã¦éžç‹¬å çš„ã«è¨±è«¾ã—ã¾ã™ã€‚ 
ï¼ˆï¼“ï¼‰ã•ã‚‰ã«ãƒ–ãƒ©ã‚¶ãƒ¼ã¯åˆ©ç”¨è€…ã«å¯¾ã—ã€ã„ã‹ãªã‚‹ç›®çš„ã®ãŸã‚ã«ã§ã‚‚æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã‚’å¤‰æ›´ã€æ”¹å¤‰ã€ç¿»è¨³ã‚ã‚‹ã„ã¯æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®æ´¾ç”Ÿç‰©ã‚’ä½œæˆã—ã€ã‹ã¤ãã‚Œã‚‰ã«ã¤ã„ã¦è¤‡è£½ã€è*²æ¸¡åŠã³å…¬è¡†é€ä¿¡ã‚’è¡Œã†æ¨©åˆ©ã‚’ç„¡å„Ÿã«ã¦éžç‹¬å çš„ã«è¨±è«¾ã—ã¾ã™ã€‚ 
ï¼ˆï¼”ï¼‰ãƒ–ãƒ©ã‚¶ãƒ¼ã«ã‚ˆã‚‹æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®é…å¸ƒãƒ»æä¾›ã¯ã€ç¾çŠ¶æœ‰å§¿ã«ã¦è¡Œã‚ã‚Œã‚‹ã‚‚ã®ã§ã‚ã‚Šã€ãƒ–ãƒ©ã‚¶ãƒ¼ã¯åˆ©ç”¨è€…ã«å¯¾ã—ã€æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã«é–¢ã—ã€æ˜Žç¤ºãƒ»é»™ç¤ºå•ã‚ãšã€ä½•ã‚‰ã®ä¿è¨¼ ï¼ˆå“è³ªä¿è¨¼ãƒ»æœ‰ç”¨æ€§ã«é–¢ã™ã‚‹ä¿è¨¼ãƒ»ç‰¹å®šç›®çš„ã¸ã®åˆè‡´ã«é–¢ã™ã‚‹ä¿è¨¼ãã®ä»–ä¸€åˆ‡å«ã‚ï¼‰ ã‚‚è¡Œã„ã¾ã›ã‚“ã€‚ 
ï¼ˆï¼•ï¼‰ãƒ–ãƒ©ã‚¶ãƒ¼ã¯æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã«é–¢ã—ã€åˆ©ç”¨è€…ã«ç”Ÿã˜ãŸã„ã‹ãªã‚‹æå®³ ï¼ˆç›´æŽ¥æå®³ãƒ»é–“æŽ¥æå®³ãƒ»ç‰¹åˆ¥æå®³ãƒ»æ´¾ç”Ÿæå®³ãƒ»æ‡²ç½°çš„æå®³ãã®ä»–ä¸€åˆ‡å«ã‚ï¼‰ ã«ã¤ã„ã¦ã‚‚ã€ã‹ã‹ã‚‹æå®³ãŒäºˆæ¸¬å¯èƒ½ã‹å¦ã‹ã€ã¾ãŸã€ãã®å¯èƒ½æ€§ã«ã¤ã„ã¦ãƒ–ãƒ©ã‚¶ãƒ¼ãŒçŸ¥ã£ã¦ã„ãŸã‹å¦ã‹ã‚’å•ã‚ãšã€è³ å„Ÿç¾©å‹™ã‚’è² ã„ã¾ã›ã‚“ã€‚ 
ï¼ˆï¼–ï¼‰ã•ã‚‰ã«ãƒ–ãƒ©ã‚¶ãƒ¼ã¯åˆ©ç”¨è€…ã«å¯¾ã—ã€ã„ã‹ãªã‚‹å ´åˆã‚‚æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®ã‚½ãƒ¼ã‚¹ã‚³ãƒ¼ãƒ‰ã‚’é–‹ç¤ºã™ã‚‹ç¾©å‹™ã‚’è² ã„ã¾ã›ã‚“ã€‚ ä¸Šè¨˜ãƒ–ãƒ©ã‚¶ãƒ¼ã«ã‚ˆã‚‹å¤‰æ›´ã€æ”¹å¤‰ã€ç¿»è¨³ã‚ã‚‹ã„ã¯æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®æ´¾ç”Ÿç‰©ä½œæˆã«é–¢ã™ã‚‹ãƒ©ã‚¤ã‚»ãƒ³ã‚¹ã¯ã€ã„ã‹ãªã‚‹å ´åˆã«ã‚‚ã€æœ¬ã‚½ãƒ•ãƒˆã‚¦ã‚§ã‚¢ã®ã‚½ãƒ¼ã‚¹ã‚³ãƒ¼ãƒ‰é–‹ç¤ºã«é–¢ã™ã‚‹ãƒ–ãƒ©ã‚¶ãƒ¼ã®é»™ç¤ºçš„ãªåŒæ„ã¨ã¯è§£é‡ˆã•ã‚Œã¾ã›ã‚“ã€‚ 

=========================================
BROTHERLICENSEJ
echo -e $MONO
fi
}


gpl_license(){
echo -e $COLOR2
cat <<GPLLICENSE
=========================================
GPL License Agreement

This Software may be used in accordance with GNU General Public License (GPL). Please read carefully the following GPL and click on "I Accept" button. If you cannot agree with the following terms, please click "I don't Accept" button. In case of your non-acceptance, you can not use this Software.
Note:
Please click on "I Accept" while holding down "Shift" or right click on "I Accept" and select "Save Target As,,," from the menu.

GNU GENERAL PUBLIC LICENSE
Version 2, June 1991

Copyright (C) 1989, 1991 Free Software Foundation, Inc.51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
Everyone is permitted to copy and distribute verbatim copies of this license document, but changing it is not allowed.

Preamble

The licenses for most software are designed to take away your freedom to share and change it. By contrast, the GNU General Public License is intended to guarantee your freedom to share and change free software--to make sure the software is free for all its users. This General Public License applies to most of the Free Software Foundation's software and to any other program whose authors commit to using it. (Some other Free Software Foundation software is covered by
the GNU Library General Public License instead.) You can apply it to your programs, too.

When we speak of free software, we are referring to freedom, not price. Our General Public Licenses are designed to make sure that you have the freedom to distribute copies of free software (and charge for this service if you wish), that you receive source code or can get it if you want it, that you can change the software or use pieces of it in new free programs; and that you know you can do these things.

To protect your rights, we need to make restrictions that forbid anyone to deny you these rights or to ask you to surrender the rights. These restrictions translate to certain responsibilities for you if you distribute copies of the software, or if you modify it.

For example, if you distribute copies of such a program, whether gratis or for a fee, you must give the recipients all the rights that you have. You must make sure that they, too, receive or can get the
source code. And you must show them these terms so they know their rights.

We protect your rights with two steps: (1) copyright the software, and (2) offer you this license which gives you legal permission to copy, distribute and/or modify the software.

Also, for each author's protection and ours, we want to make certain that everyone understands that there is no warranty for this free software. If the software is modified by someone else and passed on, we want its recipients to know that what they have is not the original, so that any problems introduced by others will not reflect on the original authors' reputations.

Finally, any free program is threatened constantly by software patents. We wish to avoid the danger that redistributors of a free program will individually obtain patent licenses, in effect making the program proprietary. To prevent this, we have made it clear that any patent must be licensed for everyone's free use or not licensed at all.

The precise terms and conditions for copying, distribution and modification follow.

GNU GENERAL PUBLIC LICENSE
TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

0. This License applies to any program or other work which contains a notice placed by the copyright holder saying it may be distributed under the terms of this General Public License. The "Program", below, refers to any such program or work, and a "work based on the Program" means either the Program or any derivative work under copyright law: that is to say, a work containing the Program or a portion of it, either verbatim or with modifications and/or translated into another language. (Hereinafter, translation is included without limitation in the term "modification".) Each licensee is addressed as "you".

Activities other than copying, distribution and modification are not covered by this License; they are outside its scope. The act of running the Program is not restricted, and the output from the Program
is covered only if its contents constitute a work based on the Program (independent of having been made by running the Program). Whether that is true depends on what the Program does.

   1. You may copy and distribute verbatim copies of the Program's source code as you receive it, in any medium, provided that you conspicuously and appropriately publish on each copy an appropriate copyright notice and disclaimer of warranty; keep intact all the notices that refer to this License and to the absence of any warranty; and give any other recipients of the Program a copy of this License along with the Program.

      You may charge a fee for the physical act of transferring a copy, and you may at your option offer warranty protection in exchange for a fee.
   2. You may modify your copy or copies of the Program or any portion of it, thus forming a work based on the Program, and copy and distribute such modifications or work under the terms of Section 1 above, provided that you also meet all of these conditions:

      a) You must cause the modified files to carry prominent notices stating that you changed the files and the date of any change.

      b) You must cause any work that you distribute or publish, that in whole or in part contains or is derived from the Program or any part thereof, to be licensed as a whole at no charge to all third parties under the terms of this License.

      c) If the modified program normally reads commands interactively when run, you must cause it, when started running for such interactive use in the most ordinary way, to print or display an
      announcement including an appropriate copyright notice and a notice that there is no warranty (or else, saying that you provide a warranty) and that users may redistribute the program under these conditions, and telling the user how to view a copy of this License. (Exception: if the Program itself is interactive but does not normally print such an announcement, your work based on the Program is not required to print an announcement.)
      
      These requirements apply to the modified work as a whole. If identifiable sections of that work are not derived from the Program, and can be reasonably considered independent and separate works in themselves, then this License, and its terms, do not apply to those sections when you distribute them as separate works. But when you distribute the same sections as part of a whole which is a work based on the Program, the distribution of the whole must be on the terms of this License, whose permissions for other licensees extend to the entire whole, and thus to each and every part regardless of who wrote it.

      Thus, it is not the intent of this section to claim rights or contest your rights to work written entirely by you; rather, the intent is to exercise the right to control the distribution of derivative or collective works based on the Program.

      In addition, mere aggregation of another work not based on the Program with the Program (or with a work based on the Program) on a volume of a storage or distribution medium does not bring the other work under the scope of this License.
   3. You may copy and distribute the Program (or a work based on it, under Section 2) in object code or executable form under the terms of Sections 1 and 2 above provided that you also do one of the following:

      a) Accompany it with the complete corresponding machine-readable source code, which must be distributed under the terms of Sections 1 and 2 above on a medium customarily used for software interchange; or,

      b) Accompany it with a written offer, valid for at least three years, to give any third party, for a charge no more than your cost of physically performing source distribution, a complete machine-readable copy of the corresponding source code, to be distributed under the terms of Sections 1 and 2 above on a medium customarily used for software interchange; or,

      c) Accompany it with the information you received as to the offer to distribute corresponding source code. (This alternative is allowed only for noncommercial distribution and only if you
      received the program in object code or executable form with such an offer, in accord with Subsection b above.)

      The source code for a work means the preferred form of the work for making modifications to it. For an executable work, complete source code means all the source code for all modules it contains, plus any associated interface definition files, plus the scripts used to control compilation and installation of the executable. However, as a special exception, the source code distributed need not include anything that is normally distributed (in either source or binary form) with the major components (compiler, kernel, and so on) of the operating system on which the executable runs, unless that component itself accompanies the executable.

      If distribution of executable or object code is made by offering access to copy from a designated place, then offering equivalent access to copy the source code from the same place counts as distribution of the source code, even though third parties are not compelled to copy the source along with the object code.
   4. You may not copy, modify, sublicense, or distribute the Program except as expressly provided under this License. Any attempt otherwise to copy, modify, sublicense or distribute the Program is void, and will automatically terminate your rights under this License. However, parties who have received copies, or rights, from you under this License will not have their licenses terminated so long as such parties remain in full compliance.
   5. You are not required to accept this License, since you have not signed it. However, nothing else grants you permission to modify or distribute the Program or its derivative works. These actions are prohibited by law if you do not accept this License. Therefore, by modifying or distributing the Program (or any work based on the Program), you indicate your acceptance of this License to do so, and all its terms and conditions for copying, distributing or modifying
      the Program or works based on it.
   6. Each time you redistribute the Program (or any work based on the Program), the recipient automatically receives a license from the original licensor to copy, distribute or modify the Program subject to these terms and conditions. You may not impose any further restrictions on the recipients' exercise of the rights granted herein. You are not responsible for enforcing compliance by third parties to this License.
   7. If, as a consequence of a court judgment or allegation of patent infringement or for any other reason (not limited to patent issues), conditions are imposed on you (whether by court order, agreement or otherwise) that contradict the conditions of this License, they do not excuse you from the conditions of this License. If you cannot distribute so as to satisfy simultaneously your obligations under this License and any other pertinent obligations, then as a consequence you may not distribute the Program at all. For example, if a patent license would not permit royalty-free redistribution of the Program by all those who receive copies directly or indirectly through you, then the only way you could satisfy both it and this License would be to refrain entirely from distribution of the Program.

      If any portion of this section is held invalid or unenforceable under any particular circumstance, the balance of the section is intended to apply and the section as a whole is intended to apply in other circumstances.

      It is not the purpose of this section to induce you to infringe any patents or other property right claims or to contest validity of any such claims; this section has the sole purpose of protecting the integrity of the free software distribution system, which is implemented by public license practices. Many people have made generous contributions to the wide range of software distributed through that system in reliance on consistent application of that system; it is up to the author/donor to decide if he or she is willing to distribute software through any other system and a licensee cannot impose that choice.

      This section is intended to make thoroughly clear what is believed to be a consequence of the rest of this License.
   8. If the distribution and/or use of the Program is restricted in certain countries either by patents or by copyrighted interfaces, the original copyright holder who places the Program under this License may add an explicit geographical distribution limitation excluding those countries, so that distribution is permitted only in or among countries not thus excluded. In such case, this License incorporates the limitation as if written in the body of this License.
   9. The Free Software Foundation may publish revised and/or new versions of the General Public License from time to time. Such new versions will be similar in spirit to the present version, but may differ in detail to address new problems or concerns.

      Each version is given a distinguishing version number. If the Program specifies a version number of this License which applies to it and "any later version", you have the option of following the terms and conditions either of that version or of any later version published by the Free Software Foundation. If the Program does not specify a version number of this License, you may choose any version ever published by the Free Software Foundation.
  10. If you wish to incorporate parts of the Program into other free programs whose distribution conditions are different, write to the author to ask for permission. For software which is copyrighted by the Free Software Foundation, write to the Free Software Foundation; we sometimes make exceptions for this. Our decision will be guided by the two goals of preserving the free status of all derivatives of our free software and of promoting the sharing and reuse of software generally.

NO WARRANTY

  11. BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU. SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.
  12. IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR REDISTRIBUTE THE PROGRAM AS PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE PROGRAM (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

END OF TERMS AND CONDITIONS

How to Apply These Terms to Your New Programs

If you develop a new program, and you want it to be of the greatest possible use to the public, the best way to achieve this is to make it free software which everyone can redistribute and change under these terms.

To do so, attach the following notices to the program. It is safest to attach them to the start of each source file to most effectively convey the exclusion of warranty; and each file should have at least the "copyright" line and a pointer to where the full notice is found.

<one line to give the program's name and a brief idea of what it does.>
Copyright (C) <year> <name of author>

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, write to the Free Software Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA


Also add information on how to contact you by electronic and paper mail.

If the program is interactive, make it output a short notice like this when it starts in an interactive mode:

Gnomovision version 69, Copyright (C) year name of author Gnomovision
comes with ABSOLUTELY NO WARRANTY; for details type \`show w'.
This is free software, and you are welcome to redistribute it
under certain conditions; type \`show c' for details.

The hypothetical commands \`show w' and \`show c' should show the appropriate parts of the General Public License. Of course, the commands you use may be called something other than \`show w' and \`show c'; they could even be mouse-clicks or menu items--whatever suits your program.

You should also get your employer (if you work as a programmer) or your school, if any, to sign a "copyright disclaimer" for the program, if necessary. Here is a sample; alter the names:

Yoyodyne, Inc., hereby disclaims all copyright interest in the program
\`Gnomovision' (which makes passes at compilers) written by James Hacker.

<signature of Ty Coon>, 1 April 1989
Ty Coon, President of Vice

This General Public License does not permit incorporating your program into proprietary programs. If your program is a subroutine library, you may consider it more useful to permit linking proprietary applications with the library. If this is what you want to do, use the GNU Library General Public License instead of this License.
=========================================
GPLLICENSE
echo -e $MONO
}

echo -e  $MONO




if [ "$1" = '-h' ] || [ "$1" = '--help' ];then
   echo -e $COLOR"$MESSAGE010"$0"$MESSAGE020"$MONO    #"USAGE:  $0  model"
   echo -e $COLOR"$MESSAGE012"$0"$MESSAGE030"$MONO    #"USAGE:  $0  -f model"
   echo -e $COLOR"$MESSAGE012"$0"$MESSAGE040"$MONO    #"USAGE:  $0  -l "
   exit 0
fi

if [ $(whoami) != 'root' ];then
    echo -e  $COLOR
    sudo  $0  $*
    if [ "$?" = 0 ];then
      echo -e  $MONO
      exit 0
    fi    
    su  -c  $0  $*
    if [ "$?" = 0 ];then
      echo -e  $MONO
      exit 0
    fi
    echo -e  $COLOR$MESSAGE050$MONO       #"Only root can do this operation."
    exit 0
fi

if [ ! -e /etc/init.d/cups ] && [ ! -e /etc/init.d/cupsys ];then 
  echo -e $COLOR$MESSAGE060$MONO                  #"CUPS is not installed."
  if [ "$1" = '' ];then
    echo -e -n $COLOR$MESSAGE240$MONO    #"Hit Return/Enter Key"
    read answer
  fi
  exit 0
fi

DOWNLOADPAGE=download_prn.html
DOWNLOADPAGEJL=driver.html
DOWNLOADPAGEJC=driver_cupswrapper.html
DOWNLOADPATH="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html"
DOWNLOADPATHJL="http://solutions.brother.co.jp/support/os/linux/lpr_printer/driver.html"
DOWNLOADPATHJC="http://solutions.brother.co.jp/support/os/linux/cups_printer/driver_cupswrapper.html"
LIB64FLT=/usr/lib64/cups/filter
LIBFLT=/usr/lib/cups/filter


TESTPRINT=/usr/share/cups/data/testprint.ps
TESTPRINT2=/usr/share/cups/data/testprint


rm -f $DOWNLOADPAGE
rm -f $DOWNLOADPAGEJL
rm -f $DOWNLOADPAGEJC

if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
  echo wget $DOWNLOADPATH
  wget $DOWNLOADPATH 2>/dev/null 1>/dev/null 
  DOWNLOADPAGEJL=''
  DOWNLOADPAGEJC=''
  DOWNLOADPAGECHK=$DOWNLOADPAGE
else
  echo wget $DOWNLOADPATHJL
  wget $DOWNLOADPATHJL 2>/dev/null 1>/dev/null 
  echo wget $DOWNLOADPATHJC
  wget $DOWNLOADPATHJC 2>/dev/null 1>/dev/null 
  DOWNLOADPAGE=''
  DOWNLOADPAGECHK=$DOWNLOADPAGEJC
fi

if [ ! -e "$DOWNLOADPAGECHK" ]  && [ "$http_proxy" = "" ];then
  echo -e -n $COLOR$MESSAGE070             #"Will you specify the PROXY server\? [y/N] ->"
  read answer
  if [ "$answer" = Y ] || [ "$answer" = y ]; then
    echo -e $COLOR$MESSAGE080         #"enter PROXY server URL "
    echo -e $COLOR$MESSAGE090         #"   ex http://\(proxy-server-url\):\(port\)"
    echo -e $COLOR$MESSAGE100         #"   ex http://\(login-name\):\(pass-word\)@\(proxy-server-url\):\(port\)"
    echo -e -n $COLOR$MESSAGE110      #"     ->"
    read proxy
  fi
  echo -e $MONO
  export http_proxy=$proxy
  if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
    echo wget $DOWNLOADPATH
    wget $DOWNLOADPATH 2>/dev/null 1>/dev/null 
    DOWNLOADPAGEJL=''
    DOWNLOADPAGEJC=''
  else
    echo wget $DOWNLOADPATHJL
    wget $DOWNLOADPATHJL 2>/dev/null 1>/dev/null 
    echo wget $DOWNLOADPATHJC
    wget $DOWNLOADPATHJC 2>/dev/null 1>/dev/null 
    DOWNLOADPAGE=''
  fi
fi

if [ ! -e "$DOWNLOADPAGE" ] && [ ! -e "$DOWNLOADPAGEJL" ] && [ ! -e "$DOWNLOADPAGEJC" ];then
  echo -e $COLOR$MESSAGE120$MONO    #"Cannot get server information. Confirm the network."
  if [ "$1" = '' ];then
    echo -e -n $COLOR$MESSAGE240$MONO    #"Hit Return/Enter Key"
    read answer
  fi
  exit 0
fi


if [ "$1" = '-l' ] || [ "$1" = '--list' ];then
  cat $DOWNLOADPAGE $DOWNLOADPAGEJC $DOWNLOADPAGEJL | \
  grep 'dlfile='   |\
  sed s/"^.*dlfile="/""/g |\
  sed s/"&lang=.*$"//g  |\
  sed s/"^.*hl"/hl/g  |\
  sed s/"^.*HL"/HL/g  |\
  sed s/"^.*mfc"/mfc/g  |\
  sed s/"^.*MFC"/MFC/g  |\
  sed s/"^.*dcp"/dcp/g  |\
  sed s/"^.*DCP"/DCP/g  |\
  sed s/"^.*fax"/fax/g  |\
  sed s/"^.*FAX"/FAX/g  |\
  sed s/"lpr.*$"//g     |\
  sed s/"-.*$"//g     |\
  sed s/"_.*$"//g     |\
  sed s/"cupswrapper.*$"//g     |\
  sed s/"cups.*$"//g     |\
  grep -v "http"  |\
  grep -v "GPL"  |\
  grep -v -i "cups"  |\
  tr '[a-z]' '[A-Z]' |\
  sort |\
  uniq
  rm -f $DOWNLOADPAGE
  rm -f $DOWNLOADPAGEJC
  rm -f $DOWNLOADPAGEJL
  exit 0
fi



if [ "$(which dpkg 2> /dev/null)" != '' ];then
  PKGCMD='dpkg  -i --force-all'
  RMPKGCMD='dpkg  -P'
  LSPKGCMD='dpkg  --list'
  EXT='\.deb'
  PKG=deb
elif [ "$(which rpm 2> /dev/null)" != '' ];then
  PKGCMD='rpm  -ihv  --nodeps'
  RMPKGCMD='rpm -e'
  LSPKGCMD='rpm -qa'
  EXT='\.rpm'
  PKG=rpm
else
  echo -e $COLOR$MESSAGE122$MONO     #"Rpm or dpkg is required."
  rm -f $DOWNLOADPAGE
  rm -f $DOWNLOADPAGEJC
  rm -f $DOWNLOADPAGEJL
  if [ "$1" = '' ];then
    echo -e -n $COLOR$MESSAGE240$MONO    #"Hit Return/Enter Key"
    read answer
  fi
  exit 0
fi

if [ "$1" = '-f' ] || [ "$1" = '--find' ];then
 MODEL=$(echo $2 | sed s/'-'//g)
elif [ "$1" = '' ];then
 echo -en $COLOR$MESSAGE121       #"Input model name->"
 read modelinput
 echo -e $MONO
 MODEL=$(echo $modelinput | sed s/'-'//g)
else
 MODEL=$(echo $1 | sed s/'-'//g)
fi

LPR=$(cat $DOWNLOADPAGE $DOWNLOADPAGEJC $DOWNLOADPAGEJL | \
  grep 'dlfile='   |\
  sed s/"^.*dlfile="/""/g |\
  sed s/"&lang=.*$"/""/g  |\
  grep $EXT  |\
  grep -i $MODEL  |\
  grep -i lpr  |\
  head -n 1)

CUPS=$(  cat $DOWNLOADPAGE $DOWNLOADPAGEJC $DOWNLOADPAGEJL  | \
  grep 'dlfile='   |\
  sed s/"^.*dlfile="/""/g |\
  sed s/"&lang=.*$"/""/g  |\
  grep $EXT  |\
  grep -i $MODEL  |\
  grep -i cups  |\
  head -n 1)




if [ "$CUPS" = '' ] || [ "$LPR" = '' ];then
  echo -e $COLOR$MESSAGE130$MONO     #"Install packages does not be found."
  echo -e $COLOR$MESSAGE140$MONO     #" Confirm the model name."
  rm -f $DOWNLOADPAGE
  rm -f $DOWNLOADPAGEJC
  rm -f $DOWNLOADPAGEJL
  if [ "$1" = '' ];then
    echo -e -n $COLOR$MESSAGE240$MONO    #"Hit Return/Enter Key"
    read answer
  fi
  exit 0
fi


if [ "$1" = '-f' ] || [ "$1" = '--find' ];then
  echo $LPR
  echo $CUPS
  rm -f $DOWNLOADPAGE
  rm -f $DOWNLOADPAGEJC
  rm -f $DOWNLOADPAGEJL
  exit 0
fi


LPRFILE=$(echo $LPR | sed s/"^.*\/"//g)
CUPSFILE=$(echo $CUPS | sed s/"^.*\/"//g)

if [ "$PKG" = deb ];then
  PREPKGCMDC="dpkg  -x $CUPSFILE /"
  PREPKGCMDL="dpkg  -x $LPRFILE /"
else
  PREPKGCMDC=''
  PREPKGCMDL=''
fi


rm -f $DOWNLOADPAGE
rm -f $DOWNLOADPAGEJC
rm -f $DOWNLOADPAGEJL


echo -e $COLOR$MESSAGE150$MONO      #"You are going to install  following packages."
echo -e $COLOR"   "$LPRFILE$MONO
echo -e $COLOR"   "$CUPSFILE$MONO
echo -e -n $COLOR$MESSAGE160        #"OK\? [y/N]  ->"

read answer
echo -e $MONO

if [ "$answer" != Y ] && [ "$answer" != y ]; then
    exit 0
fi

if ! [ -e "$LPRFILE" ];then
brother_license

echo -e -n $COLOR$MESSAGE170        #"Are you agree\? [Y/n] ->"

read answer
echo -e $MONO

if [ "$answer" = N ] || [ "$answer" = n ]; then
  exit 0
fi
rm -f $LPRFILE
wget $LPR

fi 

if ! [ -e "$CUPSFILE" ];then

gpl_license

echo -e -n $COLOR$MESSAGE180          #"Do you agree\? [Y/n] ->"
read answer
echo -e $MONO

if [ "$answer" = N ] || [ "$answer" = n ]; then
  exit 0
fi

rm -f $CUPSFILE
wget $CUPS
fi

cpu64=$(uname -m | grep "amd64")
if [ "$cpu64" = '' ];then
  cpu64=$(uname -m | grep "x86_64")
fi
if [ "$cpu64" != '' ];then
  if [ "$(which dpkg 2>/dev/null)" != '' ];then
    apt-get update
    ia32=$(dpkg -l | grep "ia32-libs")
    if [ "$ia32" = '' ];then
       apt-get install ia32-libs
    fi
    lib32=$(dpkg -l | grep "lib32stdc++6")
    if [ "$lib32" = '' ];then
       apt-get install lib32stdc++6
    fi
  fi
fi



DUMMYCUPSYS=0
DUMMYCUPS=0
DUMMYLPD=0
DUMMYLPRNG=0
if ! [ -e /etc/init.d/cupsys ];then
 DUMMYCUPSYS=1
 ln -s /etc/init.d/cups  /etc/init.d/cupsys
fi

if ! [ -e /etc/init.d/cups ];then
 DUMMYCUPS=1
 ln -s /etc/init.d/cupsys  /etc/init.d/cups
fi

if ! [ -e /etc/init.d/lpd ];then
 DUMMYLPD=1
 ln -s /etc/init.d/cupsys  /etc/init.d/lpd
fi

if ! [ -e /etc/init.d/lprng ];then
 DUMMYLPRNG=1
 ln -s /etc/init.d/cupsys  /etc/init.d/lprng
fi

mkmodeldir=0
if [ ! -e /usr/share/cups/model ];then
  mkdir -p /usr/share/cups/model
  mkmodeldir=1
fi


if [ "$PREPKGCMDL" != '' ];then
  echo  $PREPKGCMDL
  $PREPKGCMDL
fi
if [ "$PREPKGCMDC" != '' ];then
  echo  $PREPKGCMDC
  $PREPKGCMDC  
fi


$PKGCMD  $LPRFILE
$PKGCMD  $CUPSFILE



PRINTER=$(echo $CUPSFILE |\
  tr '[a-z]' '[A-Z]' |\
  sed s/"^.*HL"/HL/g  |\
  sed s/"^.*MFC"/MFC/g  |\
  sed s/"^.*DCP"/DCP/g  |\
  sed s/"^.*FAX"/FAX/g  |\
  sed s/"LPR.*$"//g     |\
  sed s/"CUPS.*$"//g     |\
  sed s/"-.*$"//g     |\
  sed s/"_.*$"//g     |\
  sed s/"CUPSWRAPPER.*$"//g)


#wait for installation end

retry='0'

while [ ! -e /etc/cups/ppd/"$PRINTER".ppd ] && [ "$retry" -le 60 ] ;do
   sleep 1
   retry=$(($retry+1))
done


# for SuSE 64
if [ "$cpu64" != "" ];then
  if [ -e "$LIB64FLT" ];then
    filter32=$(ls $LIBFLT   | grep -i $PRINTER | head -n 1)
    filter64=$(ls $LIB64FLT | grep -i $PRINTER | head -n 1)
    if [ "$filter32" != '' ] && [ "$filter64" = '' ];then
      cp "$LIBFLT"/$filter32   $LIB64FLT
      echo lpadmin -p $PRINTER -E
      lpadmin -p $PRINTER -E
    fi
  fi
fi


echo -e -n $COLOR$MESSAGE190         #"Will you specify the Device URI\? [y/N] ->"
read answer
echo -e $MONO

if [ "$answer" = y ] || [ "$answer" = Y ]; then
  duri=$(lpinfo -v  | sed s/'^.* '//g)
  i=0
  for device in $duri
  do
    echo $i: $device
    i=$(($i+1))
  done
  echo -e  $i: $MESSAGE200   #"Specify IP address."

  echo -e -n  $COLOR$MESSAGE210       #"select the number of distination Device URI. ->"
  read answer
  echo -e $MONO

  if [ "$i" != "$answer" ];then
   i=0
   for device in $duri
   do
     if [ "$i" = "$answer" ];then
       echo lpadmin -p $PRINTER -v $device -E
       lpadmin -p $PRINTER -v $device -E
     fi
     i=$(($i+1))
   done
  else
    echo -e -n $COLOR$MESSAGE220          #"  enter IP address ->"
    read ip
    echo -e $MONO
    echo lpadmin -p $PRINTER -v socket://$ip -E
    lpadmin -p $PRINTER -v socket://$ip -E
  fi
fi

if [ "$(which aa-complain  2> /dev/null)" != '' ];then
   echo -e $COLOR$MESSAGE184$MONO          #"AppArmor"
    echo  aa-complain cupsd
    aa-complain cupsd
fi

if [ "$(which setenforce  2> /dev/null)" != '' ];then
   echo -e $COLOR$MESSAGE182$MONO          #"SELinux"
   echo setenforce 0
   setenforce 0
fi 

echo -e -n $COLOR$MESSAGE230         #"Test Print \? [y/N]. ->"
read answer
echo -e $MONO

if [ "$answer" = Y ] || [ "$answer" = y ]; then
  echo  wait 5s.
  sleep 5

  if [ -e $TESTPRINT ];then
    echo lpr  -P $PRINTER $TESTPRINT
    lpr  -P "$PRINTER" "$TESTPRINT"
  elif [ -e $TESTPRINT2 ];then
    echo lpr  -P $PRINTER $TESTPRINT2
    lpr  -P "$PRINTER" "$TESTPRINT2"
  else
    echo "echo $PRINTER \| lpr  -P $PRINTER"
    echo "$PRINTER" | lpr  -P "$PRINTER"
  fi
fi

# Make uninstaller

LPRPKGNAME=$(echo $LPRFILE       |\
             sed s/"_.*$"//g     |\
             sed s/"-.*$"//g)
CUPSPKGNAME=$(echo $CUPSFILE    |\
             sed s/"_.*$"//g     |\
             sed s/"-.*$"//g)



uninstaller=uninstaller_"$PRINTER"
rm   -f $uninstaller
#
echo "#!  /bin/bash"                                 > $uninstaller

#
#rm cupswrapper driver
echo "$PREPKGCMDC"                                   >>$uninstaller
echo "$RMPKGCMD    $CUPSPKGNAME"                     >>$uninstaller
#
#rm lpd driver
echo "$PREPKGCMDL"                                   >>$uninstaller
echo "$RMPKGCMD    $LPRPKGNAME"                      >>$uninstaller


if [ "$DUMMYCUPS" = 1 ]   || \
   [ "$DUMMYCUPSYS" = 1 ] || \
   [ "$DUMMYLPD" = 1 ]    || \
   [ "$DUMMYLPRNG" = 1 ];then

echo 'if [ "$1" = "-a" ];then'                       >>$uninstaller

if [ "$DUMMYCUPS" = 1 ];then
echo '  lsc=$(ls -al /etc/init.d/cups | grep ^l )'   >>$uninstaller
echo '  if [ "$lsc" != "" ];then'                    >>$uninstaller
echo '    rm /etc/init.d/cups'                       >>$uninstaller
echo '  fi'                                          >>$uninstaller
echo ''                                              >>$uninstaller
fi

if [ "$DUMMYCUPSYS" = 1 ];then
echo '  lsc=$(ls -al /etc/init.d/cupsys | grep ^l )' >>$uninstaller
echo '  if [ "$lsc" != "" ];then'                    >>$uninstaller
echo '    rm /etc/init.d/cupsys'                     >>$uninstaller
echo '  fi'                                          >>$uninstaller
echo ''                                              >>$uninstaller
fi

if [ "$DUMMYLPD" = 1 ];then
echo '  lsc=$(ls -al /etc/init.d/lpd | grep ^l )'    >>$uninstaller
echo '  if [ "$lsc" != "" ];then'                    >>$uninstaller
echo '    rm /etc/init.d/lpd'                        >>$uninstaller
echo '  fi'                                          >>$uninstaller
echo ''                                              >>$uninstaller
fi

if [ "$DUMMYLPRNG" = 1 ];then
echo '  lsc=$(ls -al /etc/init.d/lprng | grep ^l )'  >>$uninstaller
echo '  if [ "$lsc" != "" ];then'                    >>$uninstaller
echo '    rm /etc/init.d/lprng'                      >>$uninstaller
echo '  fi'                                          >>$uninstaller
fi

echo 'fi'                                            >>$uninstaller

fi 

chmod 744 $uninstaller

if [ "$1" = '' ];then
  echo -e -n $COLOR$MESSAGE240$MONO    #"Hit Return/Enter Key"
  read answer
fi
exit 0

```

---

### Post by its_jon on 2011-05-12
Help \\:D/\\:D/

---

### Post by its_jon on 2011-05-13
Ok... an update...

Im struggling and clutching at straws.

my latest idea was to access the drive that wont boot (containing ubuntu studio) and copy over any files I can find to do with Brother to my working Unity enabled drive.

still no luck :(

could someone provide a list of the files I would have to copy over ???

please ??

:)

---

### Post by its_jon on 2011-05-14
Or.... tell me how to run the above code thanks :)

---

### Post by wgarcia on 2011-05-14
Open a folder where you downloaded the file, right-click and in the "Permissions" tab check that the file can be executed. Then open a terminal, "cd" to the folder where you have the file and write

sudo ./<name of the file>

without "<" and ">". I hope you are sure that you downloaded the file from a trusted place, it doesn't seem to contain anything funny but running under "sudo" it can do whatever to your system.

---

### Post by its_jon on 2011-05-15
Thanks for the help !

Printer now working...

:)

cheers !

---

