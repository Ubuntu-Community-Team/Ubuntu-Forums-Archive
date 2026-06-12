---
title: "Rhythmbox Alters Permissions When Saving Tag Information"
date: 2010-01-02
forum: General Help
---

### Post by jamesisin on 2010-01-02
Why is it doing this and how can I make it stop?

Permissions are typically set as rw r r and whenever I save a tag using Rhythmbox the permissions become rw _ _.  I mean, it's easy enough to force the permissions back, but I shouldn't have to.

The music is on a storage drive (internal) auto-mounted at boot in ext3 and this was happening on 8.10 and is currently happening on 9.10.

Bazaar, no?

---

### Post by jamesisin on 2010-01-04
Anybody?

---

### Post by jamesisin on 2010-01-04
Please?

---

### Post by bodhi.zazen on 2010-01-05
Permission of what file or directory ? Have you set a umask in .bashrc or elsewhere ?

---

### Post by jamesisin on 2010-01-05
I have not knowingly set a umask of any sort.

The file to which the tag was amended or altered has its permissions changed.

---

### Post by bodhi.zazen on 2010-01-05
I am sorry, but I believe this is a bug in Rhythm box :

[https://bugs.launchpad.net/rhythmbox/+bug/181742](https://bugs.launchpad.net/rhythmbox/+bug/181742)

It was triaged upstream :

[https://bugzilla.gnome.org/show_bug.cgi?id=522254](https://bugzilla.gnome.org/show_bug.cgi?id=522254)

I do not see a fix, although there was a patch (in the second link). I can not tell if the patch is working or not.

---

### Post by jamesisin on 2010-01-05
> **bodhi.zazen said:**
> It was triaged upstream :

[https://bugzilla.gnome.org/show_bug.cgi?id=522254](https://bugzilla.gnome.org/show_bug.cgi?id=522254)

I have added my information to the bug report.  Thanks for the headsup.

---

### Post by heluani on 2010-01-05
This is something the developers of Rb won't change for a while, I'm not sure even if they should care about it. Anyway, since I see you posted in the bug description upstream, I posted a patch there that solves the issue of sharing files on the same system. It is something really simple though.

```
*** metadata/rb-metadata-gst.c.orig    2009-08-02 14:13:08.000000000 -0700
--- metadata/rb-metadata-gst.c    2009-08-02 14:12:43.000000000 -0700
***************
*** 1043,1048 ****
--- 1043,1053 ----
          src = g_file_new_for_uri (tmpname);
          dest = g_file_new_for_uri (md->priv->uri);

+         g_file_copy_attributes ( dest, src, GFILE_COPY_NONE, NULL,
&io_error);
+         if (io_error != NULL) {
+             goto gio_error;
+         }
+ 
          g_file_move (src, dest, G_FILE_COPY_OVERWRITE, NULL, NULL, NULL,
&io_error);
          if (io_error != NULL) {
              goto gio_error;
```

R.

---

### Post by bodhi.zazen on 2010-01-05
> **heluani said:**
> This is something the developers of Rb won't change for a while, I'm not sure even if they should care about it. Anyway, since I see you posted in the bug description upstream, I posted a patch there that solves the issue of sharing files on the same system. It is something really simple though.

```
*** metadata/rb-metadata-gst.c.orig    2009-08-02 14:13:08.000000000 -0700
--- metadata/rb-metadata-gst.c    2009-08-02 14:12:43.000000000 -0700
***************
*** 1043,1048 ****
--- 1043,1053 ----
          src = g_file_new_for_uri (tmpname);
          dest = g_file_new_for_uri (md->priv->uri);

+         g_file_copy_attributes ( dest, src, GFILE_COPY_NONE, NULL,
&io_error);
+         if (io_error != NULL) {
+             goto gio_error;
+         }
+ 
          g_file_move (src, dest, G_FILE_COPY_OVERWRITE, NULL, NULL, NULL,
&io_error);
          if (io_error != NULL) {
              goto gio_error;
```R.

Thank you for that information and follow up, I could not determine if the patch was working on the upstream bug report.

---

### Post by jamesisin on 2010-01-05
Thanks, heluani.

I have my music stored on a server now (9.10 Desktop).  I am able to share that music across my network currently using either a Samba share or a DAAP share.  I am working to create a streaming option (debating the values of various offerings, really).

I don't suspect that your script will help me with that one, eh?  Maybe it will.  The important part is that file permissions remain rw r r (for the Samba access).

---

