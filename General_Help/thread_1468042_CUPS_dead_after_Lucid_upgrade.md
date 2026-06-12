---
title: "CUPS dead after Lucid upgrade"
date: 2010-05-01
forum: General Help
---

### Post by thechanklybore on 2010-05-01
Hi All,

Perfectly working 9.10 just upgrade to 10.04, and now CUPS won't play ball. Any time I try to add a printer with the inbuilt Printer admin utility I get the message:

There was an error during the CUPS operation: 'server-error-internal-error'

If I try and add the printer using [http://localhost:631](http://localhost:631) - any operation gives me:

631 - Request Entity Too Large

My previously installed printer has been removed automagically. Boo. So far I have:

aptitude purge cups
aptitude install cups

Which has made absolutely no difference.

Can anyone help?

Thanks

David

---

### Post by dandelo on 2010-05-06
Same error for me here, does anyone have a solution?

---

