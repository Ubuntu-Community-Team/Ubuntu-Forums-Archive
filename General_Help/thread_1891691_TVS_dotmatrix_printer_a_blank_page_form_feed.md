---
title: "TVS dotmatrix printer a blank page form feed"
date: 2011-12-06
forum: General Help
---

### Post by Vishnu V on 2011-12-06
Hi,
 TVS RP45 dot matrix printer does not work properly. It always feeds a blank page after printing. It wastes too much amount of paper.
I tried 
export LC_PAPER=a6 and  custom paper size printing. Both fails
The PPD file is
```

*PPD-Adobe: "4.3"

*%

*% For information on using this, and to obtain the required backend

*% script, consult http://www.openprinting.org/

*%

*% This file is published under the GNU General Public License

*%

*% PPD-O-MATIC (3.0.0 or newer) generated this PPD file. It is for use with 

*% all programs and environments which use PPD files for dealing with

*% printer capability information. The printer must be configured with the

*% "foomatic-rip" backend filter script of Foomatic 3.0.0 or newer. This 

*% file and "foomatic-rip" work together to support PPD-controlled printer

*% driver option access with arbitrary free software printer drivers and

*% printing spoolers.

*%

*% To save this file on your disk, wait until the download has completed

*% (the animation of the browser logo must stop) and then use the

*% "Save as..." command in the "File" menu of your browser or in the 

*% pop-up manu when you click on this document with the right mouse button.

*% DO NOT cut and paste this file into an editor with your mouse. This can

*% introduce additional line breaks which lead to unexpected results.

*%

*% You may save this file as 'Jusbill.ppd'

*%

*%

*FormatVersion:	"4.3"

*FileVersion:	"1.1"

*LanguageVersion: English 

*LanguageEncoding: ISOLatin1

*PCFileName:	"Jusbill.PPD"

*Manufacturer:  "TVS Electronics"

*Product:	"(Jusbill)"

*cupsVersion:	1.0

*cupsManualCopies: True

*cupsModelNumber:  2

*cupsFilter:	"application/vnd.cups-postscript 0 foomatic-rip"

*%pprRIP:        foomatic-rip other

*ModelName:     "TVSE Jusbill 40col"

*ShortNickName: "TVSE Jusbill 40col"

*NickName:      "TVSE Jusbill 40col"

*PSVersion:	"(3010.000) 550"

*PSVersion:	"(3010.000) 651"

*PSVersion:	"(3010.000) 652"

*PSVersion:	"(3010.000) 653"

*PSVersion:	"(3010.000) 704"

*PSVersion:	"(3010.000) 705"

*PSVersion:	"(3010.000) 800"

*LanguageLevel:	"3"

*ColorDevice:	False

*DefaultColorSpace: Gray

*FileSystem:	False

*Throughput:	"1"

*LandscapeOrientation: Plus90

*TTRasterizer:	Type42

*1284DeviceID: "MFG:OKI DATA CORP;MDL:ML320/1TURBO;CMD:EPSON,IBM,MICROLINE;DES:OKIDATA ML320/1 TURBO;DRV:Dokiibm,R1,M0,TG;"



*driverName jusbill/jusbill: ""

*driverType G/GhostScript built-in: ""

*driverUrl: "http://www.cs.wisc.edu/~ghost/doc/printer.htm"

*driverObsolete: False





*FoomaticIDs: TVSE Jusbill

*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPA&&

USE -sDEVICE=okiibm%A%Z -sOutputFile=- -"

*End



*OpenGroup: General/General



*OpenUI *PageSize/Page Size: PickOne

*OrderDependency: 100 AnySetup *PageSize

*DefaultPageSize: Letter

*PageSize 3x6/3x6       : "<</PageSize[216 432]/ImagingBBox null>>setpagedevice"

*PageSize 3x12/3x12     : "<</PageSize[216 864]/ImagingBBox null>>setpagedevice"

*PageSize Letter/4x6    : "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"

*PageSize 4x12/4x12     : "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"



*OpenUI *PageRegion: PickOne

*OrderDependency: 100 AnySetup *PageRegion

*DefaultPageRegion: Letter

*PageRegion 3x6/3x6     : "<</PageSize[216 432]/ImagingBBox null>>setpagedevice"

*PageRegion 3x12/3x12   : "<</PageSize[216 864]/ImagingBBox null>>setpagedevice"

*PageRegion Letter/4x6  : "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"

*PageRegion 4x12/4x12   : "<</PageSize[288 864]/ImagingBBox null>>setpagedevice"

*CloseUI: *PageRegion



*DefaultImageableArea: Letter

*ImageableArea 3x6/3x6  : "0 0 216 432"

*ImageableArea 3x12/3x12: "0 0 216 864"

*ImageableArea Letter/4x6: "0 0 288 432"

*ImageableArea 4x12/4x12: "0 0 288 864"



*DefaultPaperDimension: Letter

*PaperDimension 3x6/3x6: "216 432"

*PaperDimension 3x12/3x12: "216 864"

*PaperDimension Letter/4x6: "288 432"

*PaperDimension 4x12/4x12: "288 864"



*OpenUI *Resolution/Resolution: PickOne

*FoomaticRIPOption Resolution: enum CmdLine A

*OrderDependency: 100 AnySetup *Resolution

*DefaultResolution: 60x144dpi

*Resolution 60x72dpi/60x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x72dpi"

*FoomaticRIPOptionSetting Resolution=60x72dpi: " -r60x72"

*Resolution 60x144dpi/60x144 dpi: "%% FoomaticRIPOptionSetting: Resolution=60x144dpi"

*FoomaticRIPOptionSetting Resolution=60x144dpi: " -r60x144"

*Resolution 120x72dpi/120x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x72dpi"

*FoomaticRIPOptionSetting Resolution=120x72dpi: " -r120x72"

*Resolution 120x144dpi/120x144 dpi: "%% FoomaticRIPOptionSetting: Resolution=120x144dpi"

*FoomaticRIPOptionSetting Resolution=120x144dpi: " -r120x144"

*Resolution 240x72dpi/240x72 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x72dpi"

*FoomaticRIPOptionSetting Resolution=240x72dpi: " -r240x72"

*Resolution 240x144dpi/240x144 dpi: "%% FoomaticRIPOptionSetting: Resolution=240x144dpi"

*FoomaticRIPOptionSetting Resolution=240x144dpi: " -r240x144"

*CloseUI: *Resolution



*CloseGroup: General





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

Please help 
Thanks 
Vishnu V

---

### Post by phidia on 2011-12-06
Is TVS the manufactuer name? If it is then you may have problems because that name does not appear in the database at [open printing]("http://www.openprinting.org/printers/"). Check that link for more info and good luck. You might also want to look at the ubuntu printer guide [here]("https://help.ubuntu.com/11.04/serverguide/C/cups.html").

---

### Post by Vishnu V on 2011-12-24
TVS is the manufactuer name. Epson 9-Pin Series printer is selected from printer database. This solved my problem.
It seems that some also update is needed to fix the problem

Thanks

---

### Post by sparon on 2012-01-08
Hi
Thanks for your suggestion.
The Problem is solved.

---

