---
title: "White printing as yellow on Sharp laser printer since 10.04 installation"
date: 2010-05-04
forum: General Help
---

### Post by cascade98 on 2010-05-04
I have done a new installation of Ubuntu 10.04 and installed drivers for a Sharp MX2700N colour laser printer. Since doing this all white areas including page backgrounds are printing in a pale yellow. If I print a test page, all shades of all colours are fine except the whites which all print yellow.  The same happens with a later model Sharp laser printer as well.  A colleague has just done the upgrade to 10.04 and the problem has just started for him as well.  When printing a test page to a HP black and white inkjet printer the white boxes print white (not grey).

My PPD file is:

```
*PPD-Adobe: "4.3"
*%
*% For information on using this, and to obtain the required backend
*% script, consult http://www.openprinting.org/
*%
*% This file is published under the GNU General Public License
*%
*% PPD-O-MATIC (4.0.0 or newer) generated this PPD file. It is for use with 
*% all programs and environments which use PPD files for dealing with
*% printer capability information. The printer must be configured with the
*% "foomatic-rip" backend filter script of Foomatic 4.0.0 or newer. This 
*% file and "foomatic-rip" work together to support PPD-controlled printer
*% driver option access with all supported printer drivers and printing
*% spoolers.
*%
*% To save this file on your disk, wait until the download has completed
*% (the animation of the browser logo must stop) and then use the
*% "Save as..." command in the "File" menu of your browser or in the 
*% pop-up manu when you click on this document with the right mouse button.
*% DO NOT cut and paste this file into an editor with your mouse. This can
*% introduce additional line breaks which lead to unexpected results.
*%
*% You may save this file as 'Sharp-MX-2700N-pxlcolor.ppd'
*%
*%
*FormatVersion:    "4.3"
*FileVersion:    "1.1"
*LanguageVersion: English 
*LanguageEncoding: ISOLatin1
*PCFileName:    "PXLCOLOR.PPD"
*Manufacturer:    "Sharp"
*Product:    "(MX-2700N)"
*cupsVersion:    1.0
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:    "application/vnd.cups-postscript 100 foomatic-rip"
*cupsFilter:    "application/vnd.cups-pdf 0 foomatic-rip"
*%pprRIP:        foomatic-rip other
*ModelName:     "Sharp MX-2700N"
*ShortNickName: "Sharp MX-2700N pxlcolor"
*NickName:      "Sharp MX-2700N Foomatic/pxlcolor (recommended)"
*PSVersion:    "(3010.000) 550"
*PSVersion:    "(3010.000) 651"
*PSVersion:    "(3010.000) 652"
*PSVersion:    "(3010.000) 653"
*PSVersion:    "(3010.000) 704"
*PSVersion:    "(3010.000) 705"
*PSVersion:    "(3010.000) 800"
*PSVersion:    "(3010.000) 815"
*PSVersion:    "(3010.000) 850"
*PSVersion:    "(3010.000) 860"
*PSVersion:    "(3010.000) 861"
*PSVersion:    "(3010.000) 862"
*PSVersion:    "(3010.000) 863"
*PSVersion:    "(3010.000) 864"
*PSVersion:    "(3010.000) 870"
*LanguageLevel:    "3"
*ColorDevice:    True
*DefaultColorSpace: RGB
*FileSystem:    False
*Throughput:    "1"
*LandscapeOrientation: Plus90
*TTRasterizer:    Type42
*1284DeviceID: "DRV:Dpxlcolor,R1,M0,TG;"

*driverName pxlcolor: ""
*driverType G/Ghostscript built-in: ""
*driverUrl: "http://www.ghostscript.com/"
*driverObsolete: False
*driverManufacturerSupplied: False

*DefaultResolution: 1200dpi



*VariablePaperSize: False

*FoomaticIDs: Sharp-MX-2700N pxlcolor
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE%B%A%&&
Z -sOutputFile=- -"
*End

*OpenGroup: General/General

*OpenUI *PrintoutMode/Printout Mode: PickOne
*FoomaticRIPOption PrintoutMode: enum Composite A
*OrderDependency: 10 AnySetup *PrintoutMode
*DefaultPrintoutMode: Normal
*PrintoutMode Draft/Draft: "%% FoomaticRIPOptionSetting: PrintoutMode=Draft"
*FoomaticRIPOptionSetting PrintoutMode=Draft: "PrinterResolution=600x6&&
00dpi ColorModel=Color"
*End
*PrintoutMode Draft.Gray/Draft Grayscale: "%% FoomaticRIPOptionSetting: PrintoutMode=Draft.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Draft.Gray: "PrinterResolution=&&
600x600dpi ColorModel=Grayscale"
*End
*PrintoutMode Normal/Normal: "%% FoomaticRIPOptionSetting: PrintoutMode=Normal"
*FoomaticRIPOptionSetting PrintoutMode=Normal: "PrinterResolution=600x&&
600dpi ColorModel=Color"
*End
*PrintoutMode Normal.Gray/Normal Grayscale: "%% FoomaticRIPOptionSetting: PrintoutMode=Normal.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Normal.Gray: "PrinterResolution&&
=600x600dpi ColorModel=Grayscale"
*End
*PrintoutMode High/High Quality: "%% FoomaticRIPOptionSetting: PrintoutMode=High"
*FoomaticRIPOptionSetting PrintoutMode=High: "PrinterResolution=1200x1&&
200dpi ColorModel=Color"
*End
*PrintoutMode High.Gray/High Quality Grayscale: "%% FoomaticRIPOptionSetting: PrintoutMode=High.Gray"
*FoomaticRIPOptionSetting PrintoutMode=High.Gray: "PrinterResolution=1&&
200x1200dpi ColorModel=Grayscale"
*End
*CloseUI: *PrintoutMode

*OpenUI *PageSize/Page Size: PickOne
*FoomaticRIPOption PageSize: enum CmdLine A
*OrderDependency: 100 AnySetup *PageSize
*DefaultPageSize: A4
*PageSize Letter/US Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
*PageSize A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*FoomaticRIPOptionSetting PageSize=A4: " -dDEVICEWIDTHPOINTS=595 -dDEV&&
ICEHEIGHTPOINTS=842"
*End
*PageSize 11x17/11x17: "%% FoomaticRIPOptionSetting: PageSize=11x17"
*FoomaticRIPOptionSetting PageSize=11x17: " -dDEVICEWIDTHPOINTS=792 -d&&
DEVICEHEIGHTPOINTS=1224"
*End
*PageSize A3/A3: "%% FoomaticRIPOptionSetting: PageSize=A3"
*FoomaticRIPOptionSetting PageSize=A3: " -dDEVICEWIDTHPOINTS=842 -dDEV&&
ICEHEIGHTPOINTS=1191"
*End
*PageSize A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*FoomaticRIPOptionSetting PageSize=A5: " -dDEVICEWIDTHPOINTS=421 -dDEV&&
ICEHEIGHTPOINTS=595"
*End
*PageSize B5/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5"
*FoomaticRIPOptionSetting PageSize=B5: " -dDEVICEWIDTHPOINTS=516 -dDEV&&
ICEHEIGHTPOINTS=729"
*End
*PageSize Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*FoomaticRIPOptionSetting PageSize=Env10: " -dDEVICEWIDTHPOINTS=297 -d&&
DEVICEHEIGHTPOINTS=684"
*End
*PageSize EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*FoomaticRIPOptionSetting PageSize=EnvC5: " -dDEVICEWIDTHPOINTS=459 -d&&
DEVICEHEIGHTPOINTS=649"
*End
*PageSize EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*FoomaticRIPOptionSetting PageSize=EnvDL: " -dDEVICEWIDTHPOINTS=312 -d&&
DEVICEHEIGHTPOINTS=624"
*End
*PageSize EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*FoomaticRIPOptionSetting PageSize=EnvISOB5: " -dDEVICEWIDTHPOINTS=499&&
 -dDEVICEHEIGHTPOINTS=709"
*End
*PageSize EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*FoomaticRIPOptionSetting PageSize=EnvMonarch: " -dDEVICEWIDTHPOINTS=2&&
79 -dDEVICEHEIGHTPOINTS=540"
*End
*PageSize Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*FoomaticRIPOptionSetting PageSize=Executive: " -dDEVICEWIDTHPOINTS=52&&
2 -dDEVICEHEIGHTPOINTS=756"
*End
*PageSize Legal/US Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*FoomaticRIPOptionSetting PageSize=Legal: " -dDEVICEWIDTHPOINTS=612 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*OrderDependency: 100 AnySetup *PageRegion
*DefaultPageRegion: A4
*PageRegion Letter/US Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageRegion A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageRegion 11x17/11x17: "%% FoomaticRIPOptionSetting: PageSize=11x17"
*PageRegion A3/A3: "%% FoomaticRIPOptionSetting: PageSize=A3"
*PageRegion A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*PageRegion B5/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5"
*PageRegion Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*PageRegion EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*PageRegion EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*PageRegion EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*PageRegion EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*PageRegion Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*PageRegion Legal/US Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*CloseUI: *PageRegion

*DefaultImageableArea: A4
*ImageableArea Letter/US Letter: "18 36 594 756"
*ImageableArea A4/A4: "18 36 577 806"
*ImageableArea 11x17/11x17: "18 36 774 1188"
*ImageableArea A3/A3: "18 36 824 1155"
*ImageableArea A5/A5: "18 36 403 559"
*ImageableArea B5/B5 (JIS): "18 36 498 693"
*ImageableArea Env10/Envelope #10: "18 36 279 648"
*ImageableArea EnvC5/Envelope C5: "18 36 441 613"
*ImageableArea EnvDL/Envelope DL: "18 36 294 588"
*ImageableArea EnvISOB5/Envelope B5: "18 36 481 673"
*ImageableArea EnvMonarch/Envelope Monarch: "18 36 261 504"
*ImageableArea Executive/Executive: "18 36 504 720"
*ImageableArea Legal/US Legal: "18 36 594 972"

*DefaultPaperDimension: A4
*PaperDimension Letter/US Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension 11x17/11x17: "792 1224"
*PaperDimension A3/A3: "842 1191"
*PaperDimension A5/A5: "421 595"
*PaperDimension B5/B5 (JIS): "516 729"
*PaperDimension Env10/Envelope #10: "297 684"
*PaperDimension EnvC5/Envelope C5: "459 649"
*PaperDimension EnvDL/Envelope DL: "312 624"
*PaperDimension EnvISOB5/Envelope B5: "499 709"
*PaperDimension EnvMonarch/Envelope Monarch: "279 540"
*PaperDimension Executive/Executive: "522 756"
*PaperDimension Legal/US Legal: "612 1008"

*OpenUI *InputSlot/Media Source: PickOne
*FoomaticRIPOption InputSlot: enum CmdLine A
*OrderDependency: 100 AnySetup *InputSlot
*DefaultInputSlot: Default
*InputSlot Default/Printer default: "%% FoomaticRIPOptionSetting: InputSlot=Default"
*FoomaticRIPOptionSetting InputSlot=Default: " -dMediaPosition=0"
*InputSlot Tray1/Tray 1: "%% FoomaticRIPOptionSetting: InputSlot=Tray1"
*FoomaticRIPOptionSetting InputSlot=Tray1: " -dMediaPosition=3"
*InputSlot Tray2/Tray 2: "%% FoomaticRIPOptionSetting: InputSlot=Tray2"
*FoomaticRIPOptionSetting InputSlot=Tray2: " -dMediaPosition=4"
*InputSlot Tray3/Tray 3: "%% FoomaticRIPOptionSetting: InputSlot=Tray3"
*FoomaticRIPOptionSetting InputSlot=Tray3: " -dMediaPosition=5"
*InputSlot Tray4/Tray 4: "%% FoomaticRIPOptionSetting: InputSlot=Tray4"
*FoomaticRIPOptionSetting InputSlot=Tray4: " -dMediaPosition=6"
*InputSlot Tray5/Tray 5: "%% FoomaticRIPOptionSetting: InputSlot=Tray5"
*FoomaticRIPOptionSetting InputSlot=Tray5: " -dMediaPosition=7"
*InputSlot Tray6/Tray 6: "%% FoomaticRIPOptionSetting: InputSlot=Tray6"
*FoomaticRIPOptionSetting InputSlot=Tray6: " -dMediaPosition=8"
*InputSlot Tray7/Tray 7: "%% FoomaticRIPOptionSetting: InputSlot=Tray7"
*FoomaticRIPOptionSetting InputSlot=Tray7: " -dMediaPosition=9"
*InputSlot Automatic/Automatic Selection: "%% FoomaticRIPOptionSetting: InputSlot=Automatic"
*FoomaticRIPOptionSetting InputSlot=Automatic: " -dMediaPosition=1"
*InputSlot Manual/Manual Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Manual"
*FoomaticRIPOptionSetting InputSlot=Manual: " -dMediaPosition=2"
*CloseUI: *InputSlot

*OpenUI *Duplex/Double-Sided printing: PickOne
*FoomaticRIPOption Duplex: enum CmdLine A
*OrderDependency: 100 AnySetup *Duplex
*DefaultDuplex: None
*Duplex DuplexNoTumble/On (Flip on Long Edge): "%% FoomaticRIPOptionSetting: Duplex=DuplexNoTumble"
*FoomaticRIPOptionSetting Duplex=DuplexNoTumble: " -dDuplex"
*Duplex DuplexTumble/On (Flip on Short Edge): "%% FoomaticRIPOptionSetting: Duplex=DuplexTumble"
*FoomaticRIPOptionSetting Duplex=DuplexTumble: " -dDuplex -dTumble"
*Duplex None/Off: "%% FoomaticRIPOptionSetting: Duplex=None"
*FoomaticRIPOptionSetting Duplex=None: ""
*CloseUI: *Duplex

*CloseGroup: General

*OpenGroup: PrintoutMode/Printout Mode

*OpenUI *ColorModel/Color Mode: PickOne
*FoomaticRIPOption ColorModel: enum CmdLine B
*OrderDependency: 100 AnySetup *ColorModel
*DefaultColorModel: FromPrintoutMode
*ColorModel FromPrintoutMode/Controlled by 'Printout Mode': "%% FoomaticRIPOptionSetting: ColorModel=@PrintoutMode"
*ColorModel Color/Color: "%% FoomaticRIPOptionSetting: ColorModel=Color"
*FoomaticRIPOptionSetting ColorModel=Color: " -sDEVICE=pxlcolor"
*ColorModel Grayscale/Grayscale: "%% FoomaticRIPOptionSetting: ColorModel=Grayscale"
*FoomaticRIPOptionSetting ColorModel=Grayscale: " -sDEVICE=pxlmono"
*CloseUI: *ColorModel

*OpenUI *PrinterResolution/Resolution: PickOne
*FoomaticRIPOption PrinterResolution: enum CmdLine A
*OrderDependency: 100 AnySetup *PrinterResolution
*DefaultPrinterResolution: FromPrintoutMode
*PrinterResolution FromPrintoutMode/Controlled by 'Printout Mode': "%% FoomaticRIPOptionSetting: PrinterResolution=@PrintoutMode"
*PrinterResolution 300x300dpi/300 DPI: "%% FoomaticRIPOptionSetting: PrinterResolution=300x300dpi"
*FoomaticRIPOptionSetting PrinterResolution=300x300dpi: " -r300x300"
*PrinterResolution 600x600dpi/600 DPI: "%% FoomaticRIPOptionSetting: PrinterResolution=600x600dpi"
*FoomaticRIPOptionSetting PrinterResolution=600x600dpi: " -r600x600"
*PrinterResolution 1200x1200dpi/1200 DPI: "%% FoomaticRIPOptionSetting: PrinterResolution=1200x1200dpi"
*FoomaticRIPOptionSetting PrinterResolution=1200x1200dpi: " -r1200x120&&
0"
*End
*CloseUI: *PrinterResolution

*CloseGroup: PrintoutMode


*% Generic boilerplate PPD stuff as standard PostScript fonts and so on

*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(001.006S)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(001.006S)" Standard ROM
*Font AvantGarde-Demi: Standard "(001.007S)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(001.007S)" Standard ROM
*Font Bookman-Demi: Standard "(001.004S)" Standard ROM
*Font Bookman-DemiItalic: Standard "(001.004S)" Standard ROM
*Font Bookman-Light: Standard "(001.004S)" Standard ROM
*Font Bookman-LightItalic: Standard "(001.004S)" Standard ROM
*Font Courier: Standard "(002.004S)" Standard ROM
*Font Courier-Bold: Standard "(002.004S)" Standard ROM
*Font Courier-BoldOblique: Standard "(002.004S)" Standard ROM
*Font Courier-Oblique: Standard "(002.004S)" Standard ROM
*Font Helvetica: Standard "(001.006S)" Standard ROM
*Font Helvetica-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow: Standard "(001.006S)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(001.007S)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(001.006S)" Standard ROM
*Font Helvetica-Oblique: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(001.009S)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(001.007S)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(001.006S)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(001.007S)" Standard ROM
*Font Palatino-Bold: Standard "(001.005S)" Standard ROM
*Font Palatino-BoldItalic: Standard "(001.005S)" Standard ROM
*Font Palatino-Italic: Standard "(001.005S)" Standard ROM
*Font Palatino-Roman: Standard "(001.005S)" Standard ROM
*Font Symbol: Special "(001.007S)" Special ROM
*Font Times-Bold: Standard "(001.007S)" Standard ROM
*Font Times-BoldItalic: Standard "(001.009S)" Standard ROM
*Font Times-Italic: Standard "(001.007S)" Standard ROM
*Font Times-Roman: Standard "(001.007S)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(001.007S)" Standard ROM
*Font ZapfDingbats: Special "(001.004S)" Standard ROM

```

---

### Post by thomasw81 on 2010-05-07
I have the exact same problem on my Brother HL 4040 CN laser printer.. inkjet printer is working fine though.

---

### Post by Gandhy on 2010-05-14
i have the same problem with toshiba e-studio 3500c ......

and i find people with the same problem : Xerox c2424 

[http://forum.ubuntu-fr.org/viewtopic.php?id=396270](http://forum.ubuntu-fr.org/viewtopic.php?id=396270)

with 9.10 and the same version of openoffice 3.2 and the same ppd --> NO PROBLEM

---

### Post by thomasw81 on 2010-05-21
Hi Guys, I found a solution that worked for me:

[http://www.shicho.net/lamp/?p=154](http://www.shicho.net/lamp/?p=154)

---

