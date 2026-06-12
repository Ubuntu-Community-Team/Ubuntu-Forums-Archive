---
title: "LibreOffice Opening PowerPoints Incorrectly"
date: 2012-10-05
forum: General Help
---

### Post by Kirk Schnable on 2012-10-05
Also posted on LibreOffice Forums: [http://en.libreofficeforum.org/node/4476](http://en.libreofficeforum.org/node/4476)

Some PowerPoint presentations (.ppt files) seem to be trying to open in LibreOffice Writer.

When opening the file, it asks for a character encoding, then opens as a Writer document with gibberish in it.

The presentation files in question open correctly on a computer running Ubuntu 12.04 with LibreOffice 3.5.4.2 but experience this problem on a computer running Ubuntu 10.04 with LibreOffice 3.5.6.2 installed from the Launchpad PPA.

Here is one example of a PowerPoint presentation which experience this problem:
[http://www.pptpalooza.net/PPTs/AHAP/AntebellumReformers.ppt](http://www.pptpalooza.net/PPTs/AHAP/AntebellumReformers.ppt)

Has anyone seen this before?

---

### Post by Cheesemill on 2012-10-05
I've just tried this file using 3.6.2.2 and it opens as expected with Impress.

It may well be that the bug is fixed and will get rolled out during the update cycle.

---

### Post by Kirk Schnable on 2012-10-05
> **Cheesemill said:**
> I've just tried this file using 3.6.2.2 and it opens as expected with Impress.

It may well be that the bug is fixed and will get rolled out during the update cycle.

I was not aware that 3.6 was out already...

I have been using this PPA, which will probably never have 3.6:
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5)

What PPA are you using Cheesemill?

---

### Post by Cheesemill on 2012-10-05
I'm not using a PPA, I'm using the files from the LibreOffice website download page:

[http://www.libreoffice.org/download-more/](http://www.libreoffice.org/download-more/)


Edit - The official LibreOffice PPA is now at version 3.6.1, you may want to remove your PPA and try this one instead.
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by Kirk Schnable on 2012-10-05
> **Cheesemill said:**
> I'm not using a PPA, I'm using the files from the LibreOffice website download page:

[http://www.libreoffice.org/download-more/](http://www.libreoffice.org/download-more/)


Edit - The official LibreOffice PPA is now at version 3.6.1, you may want to remove your PPA and try this one instead.
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

I had some difficulties with using that PPA, because it required package versions conflicting with what was possible from the Lucid repositories.

I have updated the LibreOffice on the computer to 3.6.2 with the Deb packages from the LibreOffice website.  I will have to talk with the staff member who had this issue and find out if this fixed the problem.

Thanks

---

### Post by Kirk Schnable on 2012-10-10
It appears, thus far, that the update to 3.6.2 has fixed the problem.  Thanks for your input!

---

