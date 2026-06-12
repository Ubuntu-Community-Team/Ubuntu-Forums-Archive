---
title: "Printer driver (PPD) problems with Ubuntu 10.04 and Xerox 9201"
date: 2010-06-03
forum: General Help
---

### Post by mb_ubforums on 2010-06-03
Hi all,

I have an interesting issue that I encountered using an install of Ubuntu 10.04 and the PPD file for a Xerox ColorQube 9201 printer. This PPD doesn't come with the Ubuntu CD and I'd acquired it a while back somewhere else on the net The same PPD driver file has been working for me since Ubuntu 8.04, 8.10, 9.04 and 9.10. I recently re-installed my desktop to Ubuntu 10.04 and tried to install my printer. In the Choose Printer dialog box, I selected the "Have the PPD file" option and pointed it to my PPD file and it failed with the following message:

```

Failed to read PPD file.  Possible reason follows:
/home/mb/Desktop/xr_ColorQube9201.ppd: FAIL
      **FAIL**  Unable to open PPD file - Missing option keyword on line 30.

```The odd thing is that this file has been working on previous versions of ubuntu, and also works if you upgrade from 9.10 to 10.04 (which my friend did -- he already had the PPD setup with ubuntu 9.10 and when he upgraded to 10.04, it continued to work fine), but doesn't seem to work if I install a new version of Ubuntu 10.04.

The lines 26-30 of the PPD file look like this:
```

*JobPatchFile: "
[{
    << /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"
```

I'm also attaching the entire PPD file with this post. Can someone please tell me if I need to modify the PPD file or install some other software.

Thanks for any and all help.

---

### Post by mb_ubforums on 2010-06-03
Would you look at that... So I've been sitting around for two weeks trying to fix this and then I posted on this forum and then decided to do a bit more poking around, but found the solution by myself. 

If anyone encounters the same issue in the future, the solution is to edit the PPD file on line 26 and add a " 0":
Old:
```

*JobPatchFile: "
[{
    << /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"

```
New:
```

*JobPatchFile 0: "
[{
    << /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"

```
and then the PPD file will be accepted by Ubuntu 10.04. Note, you may have a conflict between Transparency and Color options in the various printer options, but the printer works fine for me (and I don't print Transparencies anyway and can't care less for this option anyway)

---

### Post by zivagolee on 2010-06-08
Thanks!!!

---

### Post by natholas on 2010-07-23
ah thanks so much! this saved me allot of hair loss :P

---

### Post by hosonno on 2010-08-16
thanx this also helped me

---

### Post by phyzjqk on 2010-08-17
Huge Help! Thank you very much. Can you explain why have to modify that line?

---

### Post by mercibe on 2010-12-03
Thank you so much!  It works like a charm with my Xerox Workcenter 5030 printer from Ubuntu 10.10 (maverick)

---

### Post by Pilot824 on 2011-04-01
For some reason its not working for me :confused:, still getting the same error message. Im trying to install a 5755:

```
Failed to read PPD file.  Possible reason follows:
/home/andrew/Downloads/XeroxPrinterPackageXpxx/ppd/xr_WorkCentre5735.ppd: FAIL
      **FAIL**  Unable to open PPD file - Missing option keyword on line 30.
```

Heres line 23-33:
```
*Manufacturer: "Xerox"
*ModelName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*ShortNickName: "Xerox WC 5735/5740/5745/5755/5755/5765/5775/5790"
*NickName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*Product: "(Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790)"
*PCFileName: "XR_WC5735.PPD"
*PSVersion: "(3011.106) 2300"

*JobPatchFile: 0"
[{
	<< /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"

*% Installable Options
*OpenGroup: InstallableOptions/Options Installed
```

---

### Post by kcallis on 2011-04-29
I am thankful for the solution to the ppd, but I am having another issue. I tried to send a test page, I am getting a conflict with some of the options: Specifically, Transparency Separators and Media type. I have fooled around with all of them, and still no go. The second problem is that is keeps asking me to authenticate. I have used my domain login username and password as well as my local username and password. I tell it to save the password, but it still keeps asking.

Anyone have any ideas on how to solve this issue?

---

### Post by agens on 2011-06-10
> **kcallis said:**
> I tried to send a test page, I am getting a conflict with some of the options: Specifically, Transparency Separators and Media type. I have fooled around with all of them, and still no go.

Same problem here. Anyone any ideas?

---

### Post by legendbb on 2011-07-14
Make sure to try reboot, we have just fixed one machine by reboot upon exact same error on 11.04 for Xerox WorkCenter 5755.

---

### Post by pwebster25 on 2011-08-02
> **Pilot824 said:**
> For some reason its not working for me :confused:, still getting the same error message. Im trying to install a 5755:

```
Failed to read PPD file.  Possible reason follows:
/home/andrew/Downloads/XeroxPrinterPackageXpxx/ppd/xr_WorkCentre5735.ppd: FAIL
      **FAIL**  Unable to open PPD file - Missing option keyword on line 30.
```

Heres line 23-33:
```
*Manufacturer: "Xerox"
*ModelName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*ShortNickName: "Xerox WC 5735/5740/5745/5755/5755/5765/5775/5790"
*NickName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*Product: "(Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790)"
*PCFileName: "XR_WC5735.PPD"
*PSVersion: "(3011.106) 2300"

*JobPatchFile: 0"
[{
	<< /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"

*% Installable Options
*OpenGroup: InstallableOptions/Options Installed
```

Did you ever get a solution for your workcentre 5755?  I am banging my head on the same wall.  I'm using the XR_WC5735.ppd file like you are.  I did add the 0 on line 26, as shown but it still says I have an error on line 30.

I'm using 10.04 64 Bit. This printer is on the network and I am trying to install it via LPD/LPR.

---

### Post by wastvedt on 2011-09-06
@Pilot824 and pwebster25:
I just came through here with the same problem, and the fix mentioned at the top worked for me. I noticed a difference between your posted edit and his fix. Line 26 should read ```
*JobPatchFile 0: "
``` not ```
*JobPatchFile: 0 "
```. Hope that works. As he said, though, I do have the conflicts between transparency and color settings. Did anyone get this straightened out?

Trygve

---

### Post by captain_frostbyte on 2011-09-07
> **Pilot824 said:**
> For some reason its not working for me :confused:, still getting the same error message. Im trying to install a 5755:

```
Failed to read PPD file.  Possible reason follows:
/home/andrew/Downloads/XeroxPrinterPackageXpxx/ppd/xr_WorkCentre5735.ppd: FAIL
      **FAIL**  Unable to open PPD file - Missing option keyword on line 30.
```

Heres line 23-33:
```
*Manufacturer: "Xerox"
*ModelName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*ShortNickName: "Xerox WC 5735/5740/5745/5755/5755/5765/5775/5790"
*NickName: "Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790"
*Product: "(Xerox WorkCentre 5735/5740/5745/5755/5755/5765/5775/5790)"
*PCFileName: "XR_WC5735.PPD"
*PSVersion: "(3011.106) 2300"

*JobPatchFile: 0"
[{
	<< /MediaType (Unspecified) /MediaColor (Unspecified) >> setpagedevice
} stopped cleartomark
"

*% Installable Options
*OpenGroup: InstallableOptions/Options Installed
```


I realise I'm a little late on this one.. but i would say your problem is that the name of your file and the line *PCFileName: "XR_WC5735.PPD" don't match.  just trying to get the printer to work for my self... but at a glance that could be the issue.  I'll find out soon.

---

### Post by ubuscout on 2011-09-12
Thanks really much, this one solved my issue with Xerox 5755 workcentre !

---

### Post by DaneelOlivaw on 2012-03-12
Thank you so much. Your post was very helpful.

---

### Post by andrebreiler on 2012-05-24
> **wastvedt said:**
> @Pilot824 and pwebster25:
As he said, though, I do have the conflicts between transparency and color settings. Did anyone get this straightened out?


Yes, I think so (I can't test right now for network reasons).

I've changed line 1215 from:
```
 *DefaultInterleaveColor: White 
``` to:
```
 *DefaultInterleaveColor: None 
```In addition I added after line 1258 the following
```

*InterleaveColor None/None: ""
*End

```The whole section looks now like the following:
```

*% ============================================================================
*% Interleave Media Color
*% ============================================================================
*JCLOpenUI *InterleaveColor/Colors: PickOne
*OrderDependency: 17 JCLSetup *InterleaveColor
*DefaultInterleaveColor: None
*InterleaveColor White/White: "%%OID_ATT_INTERLEAVE_COLOR \"White\";"
*End
*InterleaveColor Buff/Buff: "%%OID_ATT_INTERLEAVE_COLOR \"Buff\";"
*End
*InterleaveColor Blue/Blue: "%%OID_ATT_INTERLEAVE_COLOR \"Blue\";"
*End
*InterleaveColor Gray/Gray: "%%OID_ATT_INTERLEAVE_COLOR \"Gray\";"
*End
*InterleaveColor Green/Green: "%%OID_ATT_INTERLEAVE_COLOR \"Green\";"
*End
*InterleaveColor Ivory/Ivory: "%%OID_ATT_INTERLEAVE_COLOR \"Ivory\";"
*End
*InterleaveColor Orange/Orange: "%%OID_ATT_INTERLEAVE_COLOR \"Orange\";"
*End
*InterleaveColor Clear/Clear: "%%OID_ATT_INTERLEAVE_COLOR \"Clear\";"
*End
*InterleaveColor Other/Other: "%%OID_ATT_INTERLEAVE_COLOR \"Other\";"
*End
*InterleaveColor Pink/Pink: "%%OID_ATT_INTERLEAVE_COLOR \"Pink\";"
*End
*InterleaveColor Red/Red: "%%OID_ATT_INTERLEAVE_COLOR \"Red\";"
*End
*InterleaveColor Yellow/Yellow: "%%OID_ATT_INTERLEAVE_COLOR \"Yellow\";"
*End
*InterleaveColor Goldenrod/Goldenrod: "%%OID_ATT_INTERLEAVE_COLOR \"Goldenrod\";"
*End
*InterleaveColor Unspecified/Any Color: "%%OID_ATT_INTERLEAVE_COLOR \"Unspecified\";"
*End
*InterleaveColor Custom1/Custom 1: "%%OID_ATT_INTERLEAVE_COLOR \"Custom1\";"
*End
*InterleaveColor Custom2/Custom 2: "%%OID_ATT_INTERLEAVE_COLOR \"Custom2\";"
*End
*InterleaveColor Custom3/Custom 3: "%%OID_ATT_INTERLEAVE_COLOR \"Custom3\";"
*End
*InterleaveColor Custom4/Custom 4: "%%OID_ATT_INTERLEAVE_COLOR \"Custom4\";"
*End
*InterleaveColor Custom5/Custom 5: "%%OID_ATT_INTERLEAVE_COLOR \"Custom5\";"
*End
*InterleaveColor Custom6/Custom 6: "%%OID_ATT_INTERLEAVE_COLOR \"Custom6\";"
*End
*InterleaveColor Custom7/Custom 7: "%%OID_ATT_INTERLEAVE_COLOR \"Custom7\";"
*End
*InterleaveColor None/None: ""
*End
*JCLCloseUI: *InterleaveColor

```The background is that some constraints are defined in the PPD. One of them states  that selecting an "Interleave Color" is incompatible with selecting  any other "Media Type" than transparencies.
The above defines a color entry "None" which has a special meaning of  "not selected" which can fulfill the constraint of not having a color  selected at all if the media type is not set to transparency.

I notice there are other shortcomings in the PPD like providing a  boolean (tick box) option "Imaged" with no clear definition of context  (it relates to front and back cover).

My modified PPD file is attached (I got the original from the xerox web site in the "Printer Support Package").

---

