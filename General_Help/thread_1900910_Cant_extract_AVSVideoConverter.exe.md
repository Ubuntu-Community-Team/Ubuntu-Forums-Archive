---
title: "Cant extract AVSVideoConverter.exe"
date: 2011-12-27
forum: General Help
---

### Post by jewsoffislam on 2011-12-27
Hey guys! So I just finished downloading the TMNT movie collection and I was an idiot and didnt look to see what kind of file the movies were and ended up downloading them in .m2ts format. I'm not a computer whiz by any means and have no idea why they're running very slow and without sound. I did some researching on the web and I downloaded a file converter called AVS Video Converter and my laptop isnt letting me extract the .exe file. The error message i get says:

Archive:  /home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe
[/home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe or
          /home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe.zip, and cannot find /home/jewsoffislam/Downloads/AVS Video Converter 7.0.1.449/setup/AVSVideoConverter.exe.ZIP, period.

If anyone can help me it'd be greatly appreciated!!

---

### Post by elliotn on 2011-12-27
some .exe cannot be extracted, why not install it via wine

---

### Post by jewsoffislam on 2011-12-27
I just installed wine and tried it. This is the message I recieved:

The file '/home/jewsoffislam/Downloads/AVSVideoConverter.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Does that just mean the download is no good?

---

### Post by visakh0474 on 2012-02-09
Right click on the exe file and select properties.put a check mark in the session "allow file as executable".

It may be dangerous if the exe file contains any type of malware.So make sure that the exe file is from trusted source.

---

### Post by Mark Phelps on 2012-02-10
Do you know for a fact that this converter actually runs in Linux?

Asking because if it's not truly an executable, then it's a self-extracting archives -- and those are nearly always used for Windows apps, not Linux apps.

---

