---
title: "pdf server on ubuntu so windows PC can create secure pdf documents"
date: 2012-09-08
forum: General Help
---

### Post by greavette on 2012-09-08
Hello,

We currently have a Windows XP VM in our small office where I've installed PDF Creator. Our secretaries use Windows workstations for their daily work where I've installed to their printer list the ability to create secure PDF documents (no copy or printing etc) by pointing to pdf creator.

I'd like to remove this Windows XP from our network and install an Ubuntu solution to allow these workstations to create secure PDF's just as they do now.  I know I can use cups printing and print from windows through a Linux computer...would this work for creating PDF documents as well?

The way we currently work is we use Office (required by an application we bought...so we installed Office 2007 on these workstations) to create Word documents.  Our secreataries print these word documents and select PDF Creator which points to PDF Creator on our Windows XP that has it installed.  The Windows XP that houses PDF Creator automatically saves the files on an network share.  The secretaries have this share mapped to their profiles and retreive the newly created .pdf documents. 

I'd like to keep to the same type of system where our secretaries will print the Word documents to a pdf creator that uses a Linux solution running on an Ubuntu VM.  

I know I could have them use Libreoffice or Openoffice to create PDF files, but I'd rather they have only the one Office product on their computers.

Any links you can provide on how I would set this up would be greatly appreciated.

Thank you.

---

### Post by HermanAB on 2012-09-08
Install cupspdf.

---

### Post by greavette on 2012-09-08
Thanks Herman. Much appreciated.

Is there a forum for cups-pdf?  I didn't see one?  I'd like to read up on and if necessary ask questions about setting up cups-pdf security settings so the pdf documents we create cannot be printed or copied just like we have setup with our windows pdfcreator.

Thanks.

---

### Post by LewisTM on 2012-09-08
You can easily find CUPS-PDF documentation by Googling. You will have to share the PDF printer to the network using Samba or IPP. Those wanting to print to CUPS-PDF will have to use a generic Postscript driver in Windows.

What you might need to do is edit the /etc/cups/cups-pdf.conf file.
You will have to change the line
> Out ${HOME}/PDF
to your target network share.
Also the call to the pdfwriter will have to be modified to include some encryption options.
Locate the line starting with #GSCall, uncomment it (remove #) and add these arguments somewhere in the middle of the command 
> -sOwnerPassword=mypass -dEncryptionR=3 -dKeyLength=128 -dPermissions=65472
That should give you secure PDFs with all permissions removed.

Cheers!

---

