---
title: "Poor printing quality"
date: 2012-05-09
forum: General Help
---

### Post by Henne91 on 2012-05-09
Hi!

I'm using a Brother DCP 395-CN printer via AppSocket connected to my router to print. Since installing Ubuntu 12.04 all my PDFs and also text files created with LibreOffice Writer as well as images are totally poor quality. Not only pictures are pixelated but also text is, even from pdf documents.

Everything was fine in 11.10.

I installed the lpr-driver from Brother and cups-wrapper since this is the only way I know of to get this printer running.

Does anybody experience a similar problem or can help me to solve this issue?

Thanks in advance!

Hendrik

---

### Post by Henne91 on 2012-05-09
Just printed the test page from printing dialog. It looks fine so maybe I'm just missing some package that's passing stuff between LibreOffice/Evince and the print driver?

---

### Post by Henne91 on 2012-05-09
SOLVED: Had to change printer settings from "PDF" to "Postscript (driver level)". Now everything looks perfect again!

---

### Post by nexx on 2012-05-11
> **Henne91 said:**
> SOLVED: Had to change printer settings from "PDF" to "Postscript (driver level)". Now everything looks perfect again!

Cannot find where to do that, could you explain it a little bit more please):P

---

### Post by Henne91 on 2012-05-14
Open Print dialog, select your printer, choose "Properties" and go to tab "Device". At the bottom there are 3 selection boxes. The one on top is the one to change this setting.

However, it seems NOT to be SOLVED!

This step fixed printing from LibreOffice, but the issue still exists when printing from Evince or Firefox.

It looks like it's a problem with printing from PDF format. Since I don't use this in LibreOffice anymore the issue is gone there but native PDFs cannot be printed as Postscript and Firefox doesn't offer this option neither.

So can anybody help me on how to fix printing PDF correctly? PDFs look right on my screen but when printed text always looks the same pixelated no matter what font is used in the PDF document or web page.

---

### Post by Henne91 on 2012-05-14
Found this today: [https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/984082](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/984082)

Haven't tried it yet but looks like it could solve my problem since I'm using a Brother printer with a vendor-provided ppd file.

I'll try later on and report back here.

---

### Post by sudodus on 2012-05-14
I'm also using a Brother printer with a vendor-provided ppd file. I have the network printer HL-2250DN, and I recently installed it (from the recommended driver at the Brother website) for Lubuntu 12.04.

I just tested it with a pdf file, and the print quality is OK for me. Are you sure that the quality of the pdf file is good enough? I mean, can you check that the pdf file itself has high resolution?

Sometimes when I want to save a pdf file I have the opposite problem: I want to decrease the size of the file and I am prepared to sacrifice quality. This can be done with the following command

Type

```
gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=setting -sOutputFile=output.pdf input.pdf
```

into the Terminal window, replacing "input.pdf" with the name of your PDF file and "setting" with a desired quality level, and then press "Enter."

Quality level settings are "/screen," the lowest resolution and lowest file size, but fine for viewing on a screen; "/ebook," a mid-point in resolution and file size; "/printer" and "/prepress," high-quality settings used for printing PDFs.

Maybe you can play with the ***gs*** command and check if it has any influence on your print quality.

---

### Post by dlane on 2012-05-21
> **Henne91 said:**
> Found this today: [https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/984082](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/984082)

Haven't tried it yet but looks like it could solve my problem since I'm using a Brother printer with a vendor-provided ppd file.

I'll try later on and report back here.

This worked for me. For my Brother MFC-J415W printer, also using the Brother-provided PPD file, I altered the file /etc/cups/ppd/Brother-MFC-J415W.ppd (first I copied the original to a backup) to read as follows (I added the entire stanza "Resolution auto Features":

```
*%==== Resolution auto Features =================================                                                                                                                                
*OpenUI *Resolution/Quality: PickOne
*OrderDependency: 14 AnySetup *Resolution
*DefaultResolution: 600x600dpi
*Resolution 150x150dpi/Fast:    "          "
*Resolution 300x300dpi/Fast Normal:     "          "
*Resolution 600x600dpi/Normal:          "          "
*Resolution 1200x1200dpi/Fine:          "          "
*Resolution 1200x2400dpi/Photo:                 "          "
*Resolution 1200x6000dpi/Highest:       "          "
*CloseUI: *Resolution

*%==== Resolution Features =================================                                                                                                                                     
*OpenUI *BRResolution/Quality: PickOne
*OrderDependency: 14 AnySetup *BRResolution
*DefaultBRResolution: 600x600dpi
*BRResolution 150x150dpi/Fast:  "          "
*BRResolution 300x300dpi/Fast Normal:   "          "
*BRResolution 600x600dpi/Normal:                "          "
*BRResolution 1200x1200dpi/Fine:                "          "
...

```

The "Resolution Features" section was the original one in the file. The change is to replace each instance of BRResolution with Resolution in the copied stanza.

Hope that helps someone.

---

### Post by Henne91 on 2012-05-22
You don't have to edit your PPD file anymore. That was just a workaround.

You can now get the updated version of the package »cups-filters« from Precise-Proposed. This update will be released as regular bug fix via update manager soon.

If you need the updated package right now, read this to find out how to [enable proposed]("https://wiki.ubuntu.com/Testing/EnableProposed").

[COLOR=Red][B]WARNING: Do not install all updates from proposed since they may break your system! Only install cups-filters. Afterwards you can disable proposed.

[/B][COLOR=Black]The update for cups-filters fixed the problem for me.[/COLOR]
[/COLOR]

---

