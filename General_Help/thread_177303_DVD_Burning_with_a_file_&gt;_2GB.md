---
title: "DVD Burning with a file &gt; 2GB"
date: 2006-05-16
forum: General Help
---

### Post by mesilliac on 2006-05-16
I can't do it. After creating 4 shiny round baubles trying to get GnomeBaker or Nautilus CD/DVD Burner to work, I finally bit my lip and opened a terminal. Found out the proper syntax for growisofs, gave that a shot. After looking at the error message, and searching a bit on google, it seems the version of mkisofs provided with ubuntu 5.10 *cannot / will not* burn DVDs containing any single file greater than 2GB.

This isn't a request for help - just a note in case anyone has the same problem.

If your DVD burning programs are creating coasters with no warning, check that you're not trying to write a file greater than 2GB.

As far as I can tell, this applies to Breezy, and not Dapper.

As a side note, it would really be quite nice if Nautilus were to warn me that my file was too large, in stead of just burning an empty DVD without any apparent errors :/.

---

### Post by frodon on 2006-05-16
Strange, you should use K3B it is able to handle file > 2Go and it warn you when it see one.

---

