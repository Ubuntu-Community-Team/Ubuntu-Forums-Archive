---
title: "Reading EXIF data from TIFF files"
date: 2010-08-09
forum: General Help
---

### Post by ElSlunko on 2010-08-09
Hi Everyone,

I'm having trouble reading EXIF data from TIFF files. Both 8 bit and 16 bit fail to load EXIF data via eye of gnome and GIMP and I'm not sure why. Neither files downloaded online nor rendered from Bibble 5 seem to work.

Using Ubuntu 10.04 64bit and GIMP 2.7.2.

---

### Post by ElSlunko on 2010-08-10
Just a little update. Still not working. Tried two command line tools and got

> 
edward@Machina:~/Desktop/phusolfinals$ exif _DSC0059.tif
Corrupt data
The data provided does not follow the specification.
ExifLoader: The data supplied does not seem to contain EXIF data.


and

```
edward@Machina:~/Desktop/phusolfinals$ exiftool _DSC0059.tif
ExifTool Version Number         : 7.89
File Name                       : _DSC0059.tif
Directory                       : .
File Size                       : 70 MB
File Modification Date/Time     : 2010:08:09 12:19:58-07:00
File Type                       : TIFF
MIME Type                       : image/tiff
Exif Byte Order                 : Little-endian (Intel, II)
Image Width                     : 2860
Image Height                    : 4290
Bits Per Sample                 : 16 16 16
Compression                     : Uncompressed
Photometric Interpretation      : RGB
Strip Offsets                   : (Binary data 37959 bytes, use -b option to extract)
Orientation                     : Horizontal (normal)
Samples Per Pixel               : 3
Rows Per Strip                  : 1
Strip Byte Counts               : (Binary data 25739 bytes, use -b option to extract)
X Resolution                    : 150
Y Resolution                    : 150
Planar Configuration            : Chunky
Resolution Unit                 : inches
XMP Toolkit                     : XMP Core 4.4.0
White Balance                   : Manual
ISO Speed Rating                : 200
Rating                          : 3
Label                           : Red
Creator                         : Edward De la Torre
Subject                         : Portrait, Fashion, Clients, Phusol
Creator City                    : Torrance
Creator Country                 : USA
Creator Region                  : California
Creator Work Email              : edward@edltphoto.com
Creator Work URL                : http://edltphoto.com
Hierarchical Subject            : Portrait|Fashion, Clients|Phusol
Current IPTC Digest             : b7896dc05fd462b13919aceb6c64b4fa
Coded Character Set             : UTF8
Application Record Version      : 4
Keywords                        : Clients, Fashion, Phusol, Portrait
Date Created                    : 2010:07:24
Time Created                    : 18:28:45
By-line                         : Edward De la Torre
Make                            : NIKON CORPORATION
Camera Model Name               : NIKON D90
Modify Date                     : 2010:08:09 12:19:54
Exposure Time                   : 1/400
F Number                        : 8.0
Exposure Program                : Aperture-priority AE
ISO                             : 200
Date/Time Original              : 2010:07:24 18:28:45
Create Date                     : 2010:07:24 18:28:45
Exposure Compensation           : +2/3
Max Aperture Value              : 2.8
Metering Mode                   : Multi-segment
Light Source                    : Unknown
Flash                           : No Flash
Focal Length                    : 50.0 mm
Sub Sec Time                    : 920
Exposure Mode                   : Auto
Focal Length In 35mm Format     : 75 mm
Scene Capture Type              : Standard
Contrast                        : Normal
Saturation                      : Normal
Sharpness                       : Normal
Subject Distance Range          : Unknown
Profile CMM Type                : Lino
Profile Version                 : 2.1.0
Profile Class                   : Display Device Profile
Color Space Data                : RGB
Profile Connection Space        : XYZ
Profile Date Time               : 1998:02:09 06:49:00
Profile File Signature          : acsp
Primary Platform                : Microsoft Corporation
CMM Flags                       : Not Embedded, Independent
Device Manufacturer             : IEC
Device Model                    : sRGB
Device Attributes               : Reflective, Glossy, Positive, Color
Rendering Intent                : Media-Relative Colorimetric
Connection Space Illuminant     : 0.9642 1 0.82491
Profile Creator                 : HP
Profile ID                      : 0
Profile Copyright               : Copyright (c) 1998 Hewlett-Packard Company
Profile Description             : sRGB IEC61966-2.1
Media White Point               : 0.95045 1 1.08905
Media Black Point               : 0 0 0
Red Matrix Column               : 0.43607 0.22249 0.01392
Green Matrix Column             : 0.38515 0.71687 0.09708
Blue Matrix Column              : 0.14307 0.06061 0.7141
Device Mfg Desc                 : IEC http://www.iec.ch
Device Model Desc               : IEC 61966-2.1 Default RGB colour space - sRGB
Viewing Cond Desc               : Reference Viewing Condition in IEC61966-2.1
Viewing Cond Illuminant         : 19.6445 20.3718 16.8089
Viewing Cond Surround           : 3.92889 4.07439 3.36179
Viewing Cond Illuminant Type    : D50
Luminance                       : 76.03647 80 87.12462
Measurement Observer            : CIE 1931
Measurement Backing             : 0 0 0
Measurement Geometry            : Unknown (0)
Measurement Flare               : 0.999%
Measurement Illuminant          : D65
Technology                      : Cathode Ray Tube Display
Red Tone Reproduction Curve     : (Binary data 2060 bytes, use -b option to extract)
Green Tone Reproduction Curve   : (Binary data 2060 bytes, use -b option to extract)
Blue Tone Reproduction Curve    : (Binary data 2060 bytes, use -b option to extract)
Aperture                        : 8.0
Date/Time Created               : 2010:07:24 18:28:45
Image Size                      : 2860x4290
Scale Factor To 35 mm Equivalent: 1.5
Shutter Speed                   : 1/400
Modify Date                     : 2010:08:09 12:19:54.920
Circle Of Confusion             : 0.020 mm
Field Of View                   : 27.0 deg
Focal Length                    : 50.0 mm (35 mm equivalent: 75.0 mm)
Hyperfocal Distance             : 15.60 m
Light Value                     : 13.6

```

So clearly exiftool was able to read the exif while Eye of Gnome, exif, and GIMP were not able too.

*scratches head*

---

### Post by ElSlunko on 2010-08-11
Tiny Bump.

After doing some research it seems like some viewers don't have exif data built into their TIFF plugins.

---

