---
title: "Printing Problems LPD"
date: 2009-10-26
forum: General Help
---

### Post by Kennycl on 2009-10-26
Hi All,

Have decided to give Ubuntu a fair crack having given up with windows for dealing with lots of data.

Anyway I am having some issues printing at work in linux, so any help would be appreciated!

I am running the release candidate of 9.10 as I was having resolution issues with 9.04 due (I think) to cheap onboard intel graphics card a drivers, thankfully 9.10 solved this itself :).

I am trying to print on the office printer which is a HP 1320n laser, it is setup through a netgear printer server and I have been told to use LDP(??) to print on it. I have effectively an ip address for the device and am able to use CUPS to set the printer up, and can occasionally get it to print the first couple of pages of a PDF before it gives up, prints a page saying:

PCL XL Error:

Subsystem: Image
Error: Missing Data
Operator: ReadImage
Position: 15

and then it prints lots of test pages or rubbish!

Any help would be appreciated, printing is quite an essential function! Let me know if I can provide you with any log reports that would help (and how to get them!)

Cheers,

Kenny

---

### Post by phillw on 2009-10-26
Hi,

This thread may be of help ...

[http://ubuntuforums.org/archive/index.php/t-458376.html](http://ubuntuforums.org/archive/index.php/t-458376.html)

Regards,

Phill.

---

### Post by Kennycl on 2009-10-26
Cheers for the link Phil.

Have read through it and effectively it is the same problem I am having hit and miss printing, mostly miss mind! :) 

hmmm....

I'll keep trying, I think at least one wood so far has been lost this morning!

---

### Post by Kennycl on 2009-10-26
Problem solved, for anyone who experiences anything similar:

The postscript driver seems to fail for memory intensive pages, using the hpijis one from HP seems to have done the trick. 

Kenny

---

### Post by phillw on 2009-10-26
> **Kennycl said:**
> Problem solved, for anyone who experiences anything similar:

The postscript driver seems to fail for memory intensive pages, using the hpijis one from HP seems to have done the trick. 

Kenny


Cool, I was guessing it was a hand-shaking issue, where the computer wasn't being told to stop when the printer buffer was full. I recall it it driving us mad on a pure unix sytem some 15 years ago, as you say revised driver has sorted it for you.

Phill.

---

### Post by Bertik on 2010-02-19
> **Kennycl said:**
> Problem solved, for anyone who experiences anything similar:

The postscript driver seems to fail for memory intensive pages, using the hpijis one from HP seems to have done the trick. 

Kenny

Where can I find hpijis please?

All I can find is hpjis ......

---

### Post by tdawgpharaoh on 2010-05-28
I appear to have the same problem, but I am already using hpijs driver.

Any other possibilityes?

---

