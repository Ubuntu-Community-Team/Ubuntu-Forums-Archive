---
title: "How to clear completed print jobs in Jaunty"
date: 2009-11-11
forum: General Help
---

### Post by OrangeVixen on 2009-11-11
If you ever looked at your print jobs (**Applications->Accessories->Manage Print Jobs**) and then clicked on **View->Show Completed Jobs**, you'll probably see a really long list of completed print jobs, with or without errors.

However there is no simple way to clear this list for any reason (saving disk space, privacy, etc).

The only way that I have found, under Ubuntu 9.04 Jaunty (set up is different for other versions of Ubuntu), is to run a Terminal and go to /var/spool

```

cd /var/spool
sudo ls -Alrt cups

```

There you will see a long list of files, they're the basically what's listed in the print jobs. So all you have to do is remove those files (but not the tmp directory within it).

```

sudo rm cups/*

```

That should clear the list of completed print jobs.

If you do not want completed print jobs to be logged any more, go to **System->Administration->Printing** then go to **Server->Settings** and click on **Advanced** and selected **Do Not Preserve Job History**

---

