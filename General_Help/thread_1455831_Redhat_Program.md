---
title: "Redhat Program"
date: 2010-04-16
forum: General Help
---

### Post by bondmatt on 2010-04-16
Edit: File had redhat in name. It was probably just tested in redhat. One file was the executable, it ran once the security settings were changed to allow it to do so.

I am interested in testing some engineering software and I have been provided a gunzip file. If I unzip it I get an executable (x-executable MIME type) that by default would be opened by Wine. The file name includes the terms redhat and intel64.

Can anyone tell me what this is and if I can install it in Ubuntu (I am running 8.04)? The developer that provided it to me is away for a week. I am woefully dependent on the package manager in Linux. I would like to start changing that. On a somewhat separate note does anyone have any suggestions to that end?

Thank you,
- Matt Bondy

---

### Post by bwhite82 on 2010-04-16
What's included in the unzipped archive? What are the file extensions? .rpm? It could be source code in which you can compile it. We can't know unless you post it here.

---

### Post by wojox on 2010-04-16
If it is a .rpm you can try [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto")

---

### Post by bondmatt on 2010-04-16
The only file in the archive looks like an executable for Windows. Wine tries to run it but cannot. I would not want to run this program in Wine anyways, it is incredibly hardware intensive.

I was expecting an rpm file. I have alien. Anyway to know if the extension is wrong?

Edit: I changed the extension to .rpm and tried to use alien to convert to a Debian package. It did not work. Error message was along the lines 'not an rpm package'. Any other ideas?

I found something very interesting. This was custom compiled for me. I went to properties and under Permissions
I checked off 'Allow executing file as program'. It looks like it ran. This program in windows takes an input file, runs an analysis, and spits out output files. In this case I received error messages just like the ones in windows if something goes wrong but in this case the error messages were as expected, along the lines of 'no input file provided'. Now I just need to figure out how to give it an input file. Now that I think about it I think the developer told me how to do that.

Thanks,
- Matt Bondy

---

### Post by bwhite82 on 2010-04-16
If you don't want to post the file here, at least type in the archive's contents here. So it contains only one file with .exe at the end? If so, then it probably won't work in Linux or wine for that matter (unless someone over at Wine has worked on it already). You can check in their appdb.

---

### Post by bondmatt on 2010-04-16
The one file has no visible extension, even in the console. I think I have this sorted out (see previous post).
A quick explanation (or link to a good webpage) of what I am seeing would be appreciated.

Thanks,
- Matt Bondy

---

