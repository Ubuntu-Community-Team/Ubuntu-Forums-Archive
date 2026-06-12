---
title: "Permissions Keep Changing Themselves"
date: 2009-10-20
forum: General Help
---

### Post by xluryan on 2009-10-20
My friend has an old laptop, on which we installed 9.04.

He's using eclipse, and we're getting an error every 5 minutes or so about permissions preventing eclipse from auto-saving something or other. But that's not what's wrong...

Figuring it was a permissions thing, I told him to [FONT="Courier New"][COLOR="DarkSlateGray"]**sudo chmod -R 777 ~/workspace/**[/COLOR][/FONT], which is his eclipse workspace folder.

The command executed fine, but then all of the permission changed back to what they were immediately before the command. No matter how we set the permissions, they keep changing themselves back.

Any ideas?

---

### Post by MaindotC on 2009-10-20
Use a different folder.

---

### Post by Niko Johnson on 2009-10-20
> **strAlan said:**
> Use a different folder.
Agreed... i had a similar problem, just made a new folder and it worked just fine, thats one of thoes "stupid errors" that just slow us down

---

