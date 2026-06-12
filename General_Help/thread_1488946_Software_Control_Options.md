---
title: "Software Control Options"
date: 2010-05-20
forum: General Help
---

### Post by riph72 on 2010-05-20
Hello all,

This is an edited re-post of something I posted to the "Ubuntu Experiences" forum, it was suggested I reposted here for a better response:

[B][I]I do have a small gripe though, and it's to do with the number of  "software update" options available via the menus.  If I want to install  software I can go to the Ubuntu Software Centre for the major apps.   But, if I want to install/remove packages, I now have via  System/Administration - "Add/Remove Software" and "Synaptic Package  Manager" doing a seemingly similar task.  If I want to check for updates I have  "Software Update" and "Update Manager", which seem to do the same job.   Also for controlling access to updates etc, there are TWO entries in the  menu called "Software Sources", both doing a similar job but with a  slightly different interface.

Has anyone else noticed this rather messy situation?  It lets down an  otherwise very polished experience![/I][/B]  
Does everyone else have all these with the up-to-date Lucid?  It was suggested my configuration might be a bit messed up and that I shouldn't have all these!

Cheers,
Richard.

---

### Post by linuxman94 on 2010-05-20
Did you upgrade to lucid or do a fresh install?  If you upgraded, it seems like some of the old packages didn't get removed.

---

### Post by riph72 on 2010-05-20
It was a fresh install.  I did have a small issue with my first auto-update though, I had this lot:

[B]Error Type: <type 'exceptions.UnicodeEncodeError'>
Error Value: 'ascii' codec can't encode character u'\u2014' in position 154: ordinal not in range(128)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in <module>
    main()
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
    run(args, options.single)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
    backend.dispatcher(args)
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 710, in dispatcher
    self.dispatch_command(args[0], args[1:])
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 557, in dispatch_command
    self.get_details(package_ids)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 923, in get_details
    pkg.homepage, pkg.packageSize)
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 207, in details
    print >> sys.stdout, "details\t$s\t$s\t$s\t$s\t$s\t$ld" $ (package_id, package_license, group, desc, url, bytes)[/B]

It seemed to update ok anyway, but could this be related to why I have these unusual options?  I assume they are unusual then?

---

