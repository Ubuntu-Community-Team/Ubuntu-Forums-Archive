---
title: "Issues with gscan2pdf"
date: 2010-01-15
forum: General Help
---

### Post by Romualdou on 2010-01-15
Hi,

9.10 Karmic Koala

issue running gscan2pdf. It works fine for scanning, but I want to use it to concatenate / edit existing pdfs. But it hangs on opening PDF files (Import of picture from PDF works fine, but that's not what I need). I tried with a lot of PDF from a lot of different sources. 

I added the line "resolution = 200" in the .gscan2pdf file to solve the issue where scanned PDF won't save. 

I tried to reinstall the package with Synaptic without more success. 


Here the output with debug flag :
[B]
:~$ gscan2pdf --debug
gscan2pdf 0.9.29
Using de_DE.UTF-8 locale
Running init
Running sane_init
Gtk2-Perl version 1.221
Built for 2.18.2
Running with 2.18.3
Using GtkImageView version 1.6.1
Using Gtk2::ImageView version 0.05
Using PDF::API2 version 0.73
$VAR1 = {
          'ocr panel' => '282',
          'frontend' => 'libsane-perl',
          'Paper' => {
                       'US-Letter' => {
                                        'l' => '0',
                                        'y' => '279',
                                        'x' => '216',
                                        't' => '0'
                                      },
                       'US-Legal' => {
                                       'l' => '0',
                                       'y' => '356',
                                       'x' => '216',
                                       't' => '0'
                                     },
                       'A4' => {
                                 'l' => '0',
                                 'y' => '297',
                                 'x' => '210',
                                 't' => '0'
                               }
                     },
          'unsharp radius' => '0',
          'window_maximize' => '',
          'layout' => 'single',
          'unsharp amount' => '1',
          'cwd' => '/home/romuald/Downloads',
          'OCR output' => 'replace',
          'OCR on scan' => '1',
          'Page range' => 'all',
          'window_height' => '363',
          'rotate reverse' => '0',
          'startup warning' => '1',
          'Dark threshold' => '0.12',
          'pages to scan' => '1',
          'Blank threshold' => '0.005',
          'unpaper on scan' => '1',
          'rotate facing' => '0',
          'libsane-perl version' => '0.03',
          'cache options' => '',
          'downsample dpi' => '150',
          'window_width' => '696',
          'threshold tool' => '80',
          'window_x' => '169',
          'quality' => '75',
          'window_y' => '105',
          'unsharp sigma' => '1',
          'date offset' => '0',
          'thumb panel' => '100',
          'version' => '0.9.29',
          'unsharp threshold' => '0.05',
          'scan prefix' => '',
          'SANE version' => '1.0.20',
          'downsample' => '',
          'restore window' => '',
          'pdf compression' => 'auto'
        };
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found tesseract
Found cjb2 (djvu)
Found unpaper
Found libtiff
Using /tmp/GwsUQRnGqb for temporary files
$VAR1 = [];
Restoring session in /tmp/GwsUQRnGqb
$VAR1 = [];
Invalid header block at offset unknown at /usr/bin/gscan2pdf line 1676[/B]
(...)

(will repeat this last line a lot of time until...)

(...)
[B]Invalid header block at offset unknown at /usr/bin/gscan2pdf line 1676
No data could be read from file at /usr/bin/gscan2pdf line 1676
*** unhandled exception in callback:
***   Can't call method "list_files" on an undefined value at /usr/bin/gscan2pdf line 1677.
***  ignoring at /usr/bin/gscan2pdf line 10341.[/B]

that's it ! Any hint ?

---

### Post by Romualdou on 2010-01-22
Nobody any idea to come forward here ?

Thanks

---

### Post by Olav on 2010-01-22
> **Romualdou said:**
> Nobody any idea to come forward here ?

Thanks
My idea is this: gscan2pdf is a very nice application and I use it to scan all my correspondence, but it is not a PDF editor at all. It can't do what you seem to want. You may be better off using something like [PDFedit]("http://pdfedit.petricek.net/") (I have not used it myself).

---

### Post by Romualdou on 2010-01-23
Thanks for the hint, I will try this one.

I already tried different alternatives but did not fine the perfect solution so far.

Too bad for gscan as it is a great app (I find it much better than sane for document scanning, particularly because image compression is way better than with sane PDF export)

Regards,

---

