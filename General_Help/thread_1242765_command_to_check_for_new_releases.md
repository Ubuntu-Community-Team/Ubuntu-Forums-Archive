---
title: "command to check for new releases"
date: 2009-08-17
forum: General Help
---

### Post by bwitherell on 2009-08-17
Hello all,

Does anyone know of a command to check for new Ubuntu releases?

Thanks,
Brad

---

### Post by Bachstelze on 2009-08-17
There is none. However, a new release is made every 6 months, so you can't miss it. ;)

---

### Post by bwitherell on 2009-08-17
> **HymnToLife said:**
> There is none. However, a new release is made every 6 months, so you can't miss it. ;)

Yea.... that's what I thought. :cry: I was hoping there would be one though so I can automate most of the upgrade process.

Thanks,
Brad

---

### Post by sasho_zl on 2009-08-17
The command is: update-manager -d

---

### Post by bluelamp999 on 2009-08-17
This may not be what you're looking for, but...

System>Administration>Software Sources

On the Update tab, set Release upgrade section to 'Normal releases'

New releases then show up as they're released (if you have automatic updates set to 'on')

---

### Post by bwitherell on 2009-08-17
> **sasho_zl said:**
> The command is: update-manager -d

I think that requires Gnome or some other graphical environment. I need to be able to run this in a SSH terminal.

Thanks,
Brad

---

### Post by slakkie on 2009-08-17
This is what I use:

```

purge_pkg () {
        sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
        sudo aptitude clean
}

safe_upgrade() {
    local date_stamp=$(stat -c "%Z" /var/cache/apt/pkgcache.bin)
    local now=$(date "+%s")
    now=$((now - 3600))
    [ $date_stamp -lt $now ] || [ -n "$1" ] && sudo aptitude update && sudo apt-file update
    sudo aptitude safe-upgrade && purge_pkg
}

release_upgrade() {
    safe_upgrade && sudo aptitude install update-manager-core && sudo do-release-upgrade
}

```

Or you could apply this patch, against do-release-upgrade for a check.
```

--- /usr/bin/do-release-upgrade 2009-07-24 16:48:14.000000000 +0200
+++ do-release-upgrade  2009-08-17 22:03:16.000000000 +0200
@@ -38,6 +38,11 @@
   parser.add_option ("-s","--sandbox", action="store_true", default=False,
                      help=_("Test upgrade with a sandbox aufs overlay"))

+  parser.add_option ("-c", "--check-dist-upgrades", action="store_true",
+           dest="check_dist_upgrades", default=False,
+           help=_("Check if a new distribution release is available"))
+
+
   (options, args) = parser.parse_args()

   print _("Checking for a new ubuntu release")
@@ -47,9 +52,14 @@
   while m.downloading:
          time.sleep(0.5)
   if m.new_dist is None:
-         print _("No new release found")
-         sys.exit(1)
+    print _("No new release found")
+    sys.exit(1)
   # we have a new dist
+
+  if options.check_dist_upgrades:
+        print _("Upgrade possible")
+        sys.exit(0)
+
   progress = apt.progress.TextFetchProgress()
   fetcher = DistUpgradeFetcherCore(new_dist=m.new_dist,
                                   progress=progress)

```

After you apply this patch you can do the following:

sudo do-release-upgrade -c && sudo do-release-upgrade

However, you still need some manual actions to actually upgrade.

---

### Post by bwitherell on 2009-08-18
do-release-upgrade is exactly what i was looking for. Thanks.:P

---

