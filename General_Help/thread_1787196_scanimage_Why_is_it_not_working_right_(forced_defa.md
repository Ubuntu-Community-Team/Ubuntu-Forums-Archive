---
title: "scanimage: Why is it not working right (forced default geometry)"
date: 2011-06-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-20
edit:
the 1st command fails but the second command works
```
chad@lucid-desktop:~$ scanimage -d "hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1" -l 0 -t 0 -x 215.9 -y 297.011 --resolution 75 --mode Color --format=ppm > ~/Desktop/scan.ppm
scanimage: setting of option --br-y failed (Invalid argument)
chad@lucid-desktop:~$ scanimage -d "hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1" --resolution 75 --mode Color --format=ppm > ~/Desktop/scan.ppm
chad@lucid-desktop:~$
```
end edit
this fails *scanimage: setting of option --br-y failed (Invalid argument)*
```
scanimage -d "hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1" -l 0 -t 0 -x 215.9 -y 297.011 --resolution 75 --mode Color --format=ppm > ~/Desktop/scan.ppm
```this should be the same thing as
```
scanimage -d "hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1" --resolution 75 --mode Color --format=ppm  > ~/Desktop/scan.ppm
```since i merely specified to use the default size

if i use 297.01 for -y it works but not 297.011 why can't i tell it to include that 1/100 of a millimeter manually but i can automatically
i am using this form a script and some scanners defaults are not full scan i have to force full size for full scan
```
from my UMAX 3450 flatbed scanner
    -l 0..215mm [0]
        Top-left x position of scan area.
    -t 0..297mm [0]
        Top-left y position of scan area.
    -x 0..215mm [**103**]
        Width of scan-area.
    -y 0..297mm [**76.21**]
        Height of scan-area.
``````
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1':
  Scan mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 75|100|200|300|600|1200dpi [75]
        Sets the resolution of the scanned image.
    --source Flatbed [Flatbed]
        Selects the scan source (such as a document-feeder).
  Advanced:
    --contrast -127..127 [0]
        Controls the contrast of the acquired image.
    --compression JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [inactive]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
  Geometry:
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..297.011mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [**215.9**]
        Width of scan-area.
    -y 0..297.011mm [**297.011**]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    plustek:libusb:003:002
    hpaio:/usb/Deskjet_2050_J510_series?serial=CN14D3N0PQ05D1
```

---

### Post by pqwoerituytrueiwoq on 2011-06-21
anyone have any idea?
edit
if i set Y over 
297.01068878173825282^9
it gives a error and will not scan
but the default scan size for Y is 297.011

---

### Post by pqwoerituytrueiwoq on 2011-06-22
:popcorn: watching paint dry on the forums

---

