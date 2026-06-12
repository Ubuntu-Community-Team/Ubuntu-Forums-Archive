---
title: "Software Updating Error (10.04)"
date: 2010-05-17
forum: General Help
---

### Post by riph72 on 2010-05-17
Hello all,

I had this error during the auto-update process:

Error Type: <type 'exceptions.UnicodeEncodeError'>
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
    print >> sys.stdout, "details\t$s\t$s\t$s\t$s\t$s\t$ld" $ (package_id, package_license, group, desc, url, bytes)


No idea what this all means, but the update seemed to continue successfully anyway.

Anyone have any idea about this?

Cheers,
Richard.

---

