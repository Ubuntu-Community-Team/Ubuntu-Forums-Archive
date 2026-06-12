---
title: "File Format for capifax"
date: 2011-11-17
forum: General Help
---

### Post by oliwel on 2011-11-17
Hi,

I upgraded to 11.10 and unfortunatley now my beloved capisuite fax server is gone =(

I was successful in replaceing the receiving side with the capifaxrcvd but I am unable to figure out how to create a fax-file for the "capifax" tool. In the (very incomplete) docs its "Tiff G3", so I tried
pdftoppm -mono and then ppmtotiff -c g3, which results in a file that gimp can show properly but when I put this into capifax (capifax destno fax.sff) the receiving side gets only control data on the fax.

So, anybody can point me to a working solution? Its a bnit urgent as we use this faxbridge in a customers gateway...
Also any help to get capisuite back is appreciated (build from source crashes due to changes in python headers....)

Oliver

---

