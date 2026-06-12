---
title: "a command to replace mkisofs + cdrecord?"
date: 2009-09-16
forum: General Help
---

### Post by frenchn00b on 2009-09-16
In one line, can we burn from cmd line?


```
Creating an ISO image using mkisofs

    If you need to generate your own ISO, mkisofs is a great tool for doing it. You don't need fancy tools or GUI front ends to use it, either (though you may wish to employ your favorite graphical file manager). Just follow these simple steps:

       1.

          Create a temporary directory from which the ISO's files will be read.
       2.

          Insert files into that directory and arrange them in the manner you would like them to appear in the ISO.
       3.

          From a directory outside of the tempoary ISO directory, run the following command:

              mkisofs -f -R -r -l -J -Vvolid -Aappid -Ppubid -odest.iso src 

          where

          volid
              is the volume ID to be written into the master block;
          appid
              describes the application contained within the ISO;
          pubid
              names the publisher of the ISO (CD-ROM), usually including adequate contact information, such as a phone number or email address;
          dest.iso
              is the destination filename of the newly created ISO image;
          src
              is the temporary ISO directory containing the files and file structure you wish to have included in the ISO image.

       4.

          These parameters are good defaults. You can customize them, however. For more information, see man mkisofs.

Writing an ISO to a CD-ROM using cdrecord

    Assuming that all you want to do is create a CD based on the ISO 9660 file system standard, you can quickly burn the CD using the following command:

        cdrecord -v -pad speed=1 dev=0,0,0 src.iso 

    src.iso is the source filename of the ISO you are burning to the CD-ROM.

    You may need to adjust the dev parameter if you are not burning with an IDE drive or you did not follow the instructions given in Configuring an IDE/ATAPI CD-ROM burner in RedHat Linux 6.1.

    If you want, you can take the ISO image from stdin by replacing the filename with a hyphen ("-"). This works well with mkisofs if you replace the output image filename to that command with a hyphen also. Then you can chain the two commands together using a standard Unix pipe. Burning CD-ROMs in this manner reduces the total amount of temporary storage you will need, which may be useful if you are low on disk space.

Burning Audio CDs using cdrecord

    Burning audio CDs using cdrecord is a piece of cake, too. Just follow these steps:

       1.

          Create your audio tracks and store them as uncompressed, 16-bit stereo .wav files.
       2.

          Name the audio files in a manner that will cause them to be listed in the desired track order when listed alphabetically, such as 01.wav, 02.wav, 03.wav, etc.
       3.

          Change into the directory containing the wave files and make sure there are not any wave files you do not want included in the CD.
       4.

          With a blank CD in your burner, issue the following command:

              cdrecord -v -pad speed=1 dev=0,0,0 -dao -audio -swab *.wav 

          Again, you may need to adjust your dev parameter as mentioned earlier.

Copyright © 2000 Sharkysoft. All rights reserved.


```

---

### Post by KeyserSoze93 on 2009-09-16
it works fine to pipe from mkisofs to wodim (and presumably cdrecord), i.e.:
```
mkisofs -R -J folder|wodim -v -speed=16 -
```

---

### Post by frenchn00b on 2009-09-16
> **KeyserSoze93 said:**
> it works fine to pipe from mkisofs to wodim (and presumably cdrecord), i.e.:
```
mkisofs -R -J folder|wodim -v -speed=16 -
```

and couldnt we use both growisofs too? 
I mean growisfofs does a great job. 
Mkisofs causes errors usually, before burning. hemce growisofofs was invented :) it is also time consumming savnig. 

Isnt any application unter non x that does similar good job? two commands for burning that s sure strange. 

How does k3b then? it doesnt make 2 command, but does one single, just.

Have you looked the logs of K3B while/after burning a cdrom? K3b is really nice program, although it is not powerful as clonecd

---

