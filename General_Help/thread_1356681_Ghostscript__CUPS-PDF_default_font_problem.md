---
title: "Ghostscript / CUPS-PDF default font problem"
date: 2009-12-16
forum: General Help
---

### Post by c.sommer on 2009-12-16
I'm using CUPS-PDF with Ubuntu 9.10 to take anything I print to the CUPS-PDF printer and send it to a folder with a filename format of (Jobname_YYYYMMDD_HHMMSS.pdf).

I've got everything working through configuring the "CUPS-PDF.conf" and making a few changes to the "apparmor.d/usr.sbin.cupsd" file, although I'm pretty sure I set apparmor to ignore cups altogether.

To add another twist to all this I'm using an xinetd.d LPR daemon to take print jobs from an HP3000 mainframe running MPE/iX.

Anyway, I've got the PDFs naming correctly and showing up in the directory I want them to, but here's the problem:

The PDFs are not searchable, I'm not too sure why.  The pages aren't images, they are created using FreeMono and FreeMonoBold embedded fonts.  I'm wondering if font encoding could be my problem. When I select a line of text from the PDF and try to paste it (In Windows)  I get "special" characters like windows has no idea what font to use -> &#1048663;&#1048648;&#1048662;&#1048663;

So, here's the question... Does anyone know how to change the default font that Ghostscript / CUPS-PDF will use to create a PDF from an LPR text stream?  I think I need to go from a default of FreeMono and FreeMonoBold to Courier_New and Courier_New_Bold, but I don't know where to change that...

Any help would be appreciated
Thanks,

**_cups-pdf.conf:_**

```
#  cups-pdf.conf -- CUPS Backend Configuration (version 2.5.0, 2009-01-26)
#  18.09.2005, Volker C. Behr
#  Experimentelle Physik V, Universitaet Wuerzburg
#  behr@physik.uni-wuerzburg.de
#  http://www.cups-pdf.de
#
#
#  This code may be freely distributed as long as this header
#  is preserved. Changes to the code should be clearly indicated.  
#
#  This code is distributed under the GPL.
#  (http://www.gnu.org/copyleft/gpl.html)
#
#  For more detailed licensing information see cups-pdf.c in the
#  corresponding version number.                        

###########################################################################
#                                      #
# This is the configuration file for CUPS-PDF. Values that are not set in #
# here will use the defaults. Changes take effect immediately without the #
# need for restarting any services.                      #
#                                      #
# Take care not to add whitespaces at the end of a line!          #
#                                      #
###########################################################################


###########################################################################
#                                      #
# Path Settings                                  #
#                                      #
###########################################################################

### Key: Out
##  CUPS-PDF output directory
##  special qualifiers:
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash!
### Default: /var/spool/cups-pdf/${USER}

Out /pdf

### Key: AnonDirName
##  ABSOLUTE path for anonymously created PDF files
##  if anonymous access is disabled this setting has no effect
### Default: /var/spool/cups-pdf/ANONYMOUS

AnonDirName /pdf

### Key: Spool
##  CUPS-PDF spool directory - make sure there is no user 'SPOOL' on your
##  system or change the path   
### Default: /var/spool/cups-pdf/SPOOL

#Spool /var/spool/cups-pdf/SPOOL


###########################################################################
#                                      #
# Filename Settings                              #
#                                      #
###########################################################################

### Key: Truncate
##  truncate long filenames to a maximum of <Truncate> characters
##  this does not consider the full path to the output but only the filename
##  without the .pdf-extension or a job-id prefix (see 'Label')
##  the minimal value is 8
### Default: 64

#Truncate 64

### Key: Cut
##  removing file name extensions before appending .pdf to output
##  extensions will only be removed if _both_ the following criteria are met:
##   - the extension (w/o the dot) is not longer than <Cut> characters
##   - the remaining filename has a minimal length of 1 character
##  set Cut to -1 in order to disable cutting
##  recommended values: pure UNIX environment : -1
##                      mixed environments    :  3
### Default: 3

#Cut 3

### Key: Label
##  label all jobs with a unique job-id in order to avoid overwriting old
##  files in case new ones with identical names are created; always true for
##  untitled documents
##  0: label untitled documents only, 1: label all documents
### Default: 0

Label 0

### Key: TitlePref
##  where to look first for a title when creating the output filename
##  (title in PS file or title on commandline):
##  0: prefer title from %Title statement in the PS file
##  1: prefer title passed via commandline
### Default: 0

#TitlePref 0


###########################################################################
#                                      #
# User Settings                                  #
#                                      #
###########################################################################

### Key: AnonUser
##  uid for anonymous PDF creation (this might be a security issue)
##  this setting has no influence on AnonDirName (see there)
##  set this to an empty value to disable anonymous
### Default: nobody

#AnonUser nobody

### Key: LowerCase
##  This options allows to check user names given to CUPS-PDF additionally
##  against their lower case variants. This is necessary since in some
##  Windows environments only upper case user names are passed. Usually UNIX
##  user names are all lower case and it is save to use this option 
##  but be aware that it can lead to mis-identifications in case
##  you have user names that differ only in upper/lower case.
##     check only against user name as passed to CUPS  : 0
##     check additionally against lower case user name : 1
### Default: 1

#LowerCase 1

### Key: UserPrefix
##  some installations require a domain prefix added to the user name
##  leave empty for no prefix
### Default: <empty>

#UserPrefix

### Key: DirPrefix
##  if a prefix was defined above this switch toggels whether to include
##  the prefix in the output directory's name (if not $HOME) or not
##  0: do not include, 1: include
### Default: 0

#DirPrefix 0

### Key: RemovePrefix
##  some installation pass usernames with a prefix (usually a domain name)
##  if you do not want this prefix to be used by the ${USER} variable for
##  output directories put the part which is to be cut here
### Default: <empty>

#RemovePrefix


###########################################################################
#                                      #
# Security Settings                              #
#                                      #
###########################################################################

### Key: AnonUMask
##  umask for anonymous output
##  these are the _inverse_ permissions to be granted
### Default: 0000

#AnonUMask 0000

### Key: UserUMask
##  umask for user output of known users
##  changing this can introduce security leaks if confidential
##  information is processed!
### Default: 0077

#UserUMask 0077

### Key: Grp
##  group cups-pdf is supposed to run as - this will also be the gid for all
##  created directories and log files
### Default: lp

Grp lpadmin

###########################################################################
#                                      #
# Log Settings                                  #
#                                      #
###########################################################################

### Key: Log
##  CUPS-PDF log directory
##  set this to an empty value to disable all logging
### Default: /var/log/cups

#Log /var/log/cups

### Key: LogType
##  log-mode
##  1: errors
##  2: status (i.e. activity)
##  4: debug - this will generate a lot of log-output!
##  add up values to combine options, i.e. 7 is full logging
##  if logging is disabled these setting have no effect
### Default: 3

LogType 4


###########################################################################
#                                      #
# PDF Conversion Settings                          #
#                                      #
###########################################################################

### Key: GhostScript
##  location of GhostScript binary (gs)
##  MacOSX: for using pstopdf (recommended) set this to /usr/bin/pstopdf
##          or its proper location on your system
### Default: /usr/bin/gs

GhostScript /usr/bin/gs

### Key: GSTmp
##  location of temporary files during GhostScript operation
##  this must be user-writable like /var/tmp or /tmp !
### Default: /var/tmp

GSTmp /var/tmp

### Key: GSCall
## command line for calling GhostScript (!!! DO NOT USE NEWLINES !!!)
## MacOSX: for using pstopdf set this to %s %s -o %s %s
### Default: %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

### Key: PDFVer
##  PDF version to be created - can be "1.5", "1.4", "1.3" or "1.2"
##  MacOSX: for using pstopdf set this to an empty value
### Default: 1.4

#PDFVer 1.4

### Key: PostProcessing
##  postprocessing script that will be called after the creation of the PDF
##  as arguments the filename of the PDF, the username as determined by
##  CUPS-PDF and the one as given to CUPS-PDF will be passed
##  the script will be called with user privileges
##  set this to an empty value to use no postprocessing
### Default: <empty>

PostProcessing /usr/local/bin/cups-pdf-renamer.sh


###########################################################################
#                                                                         #
# Experimental Settings                                                   #
#   These settings activate experimental options. If you decide to use    #
#   them I would appreciate any feedback - including an 'ok' if they      #
#   work as expected - so I can eventually put them into the non-         #
#   experimental sections.                          #
#                                                                         #
###########################################################################

### Key: DecodeHexStrings
##  this option will try to decode hex strings in the title to allow
##  internationalized titles
##  (have a look at contrib/pstitleconv for a suitable filter for data
##   from Windows clients)
##  0: disable, 1: enable
### Default: 0

#DecodeHexStrings 0

```_**Post Processing Script:**_

```

#!/bin/sh
FILENAME=`basename $1`
DIRNAME=`dirname $1`
DATE=$(date +%Y%m%d_%H%M%S)

NOEXTFILENAME=`basename $1 .pdf`

mv $1 $DIRNAME"/"$NOEXTFILENAME"_"$DATE".pdf"

```

---

### Post by c.sommer on 2009-12-17
I've gotten a little closer to what my issue may be...
It definitely has to do with the way the embedded fonts in the PDF are encoded.

I was able to get the PDF encoding to change by switching from the default 
"CUPS-PDF Postscript driver" to the "Generic Postscript driver" in Ubuntu.

For some reason when using the "CUPS-PDF driver" the fonts are 
[TrueType (CID), Type-H encoded] when embedded into the PDF. 
When I copy the word "test" from a pdf and paste it I get: &#1048663;&#1048648;&#1048662;&#1048663;

When using the "Generic Postscript driver" the fonts are 
[TrueType, Custom encoded] when embedded into the PDF.
When I copy the word "test" from a pdf and paste it I get: WHVW

I think I need to find a way to embed the font as [TrueType, ANSI encoded]

Does anyone have any recommendations?  I'm running out of ideas...

Thanks,
Chris

Here are sample PDF files with my encoding problems:

---

### Post by fasz3d on 2012-08-13
I have a just installed a Ubuntu 12.04, it has the exact problem as well.  I tried to google around for answers, doesn't seem like there is a solution so far.

---

### Post by oldos2er on 2012-08-13
Hi fasz3d, please start a new thread for your question, this one's three years old.

---

