---
title: "Fixing screen brightness issue in Ubuntu 12.04"
date: 2012-04-27
forum: General Help
---

### Post by rfictus on 2012-04-27
This is a fix for Vaio VPCCW16FG quick key Fn F5+F6 brightness bar move but backlight no change.

To rectify this, follow the following procedure:

1) Go to [https://github.com/guillaumezin/nvidiabl/downloads](https://github.com/guillaumezin/nvidiabl/downloads) and download the nvidia dkms. As of today it is (nvidiabl-dkms_0.73_all.deb &#8212; 0.73 deb for Debian based distributions)

> wget [https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.73_all.deb](https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.73_all.deb)

Unpack it!

> sudo dpkg -i nvidiabl-dkms_0.73_all.deb

2)Discover version number of your gnome-settings-daemon.

> dpkg-query -W -f '${Version}\n' gnome-settings-daemon

Alternatively, can do through Synaptic Package Manager. If no Synaptic installed, code:

> sudo apt-get install synaptic

When in Synaptic, in the search bar, type gnome-settings-daemon to find version number.

3) Download the relevant daemon: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/)

4) Go to the directory where you unpacked it and edit the 'gsd-backlight-helper.c' file. Example:

> sudo gedit ~/gnome-settings-daemon-3.4.1/plugins/power/gsd-backlight-helper.c

Replace all code with the following:

> /* -*- Mode: C; tab-width: 8; indent-tabs-mode: t; c-basic-offset: 8 -*-
 *
 * Copyright (C) 2010-2011 Richard Hughes <richard@hughsie.com>
 *
 * Licensed under the GNU General Public License Version 2
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
 */

#include "config.h"

#include <unistd.h>
#include <glib-object.h>
#include <locale.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <string.h>

#define GSD_BACKLIGHT_HELPER_EXIT_CODE_SUCCESS			0
#define GSD_BACKLIGHT_HELPER_EXIT_CODE_FAILED			1
#define GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID	3
#define GSD_BACKLIGHT_HELPER_EXIT_CODE_INVALID_USER		4

#define GSD_BACKLIGHT_HELPER_SYSFS_LOCATION			"/sys/class/backlight"

static gchar *
gsd_backlight_helper_get_best_backlight ()
{
	gchar *filename;
	guint i;
	gboolean ret;
	GDir *dir = NULL;
	GError *error = NULL;
	const gchar *first_device;

	/* available kernel interfaces in priority order */
	static const gchar *backlight_interfaces[] = {
		"nv_backlight",
		"asus_laptop",
		"toshiba",
		"eeepc",
		"thinkpad_screen",
		"acpi_video1",
		"mbp_backlight",
		"acpi_video0",
		"fujitsu-laptop",
		"nvidia_backlight",
		"samsung",
		NULL,
	};

	/* search each one */
	for (i=0; backlight_interfaces[i] != NULL; i++) {
		filename = g_build_filename (GSD_BACKLIGHT_HELPER_SYSFS_LOCATION,
					     backlight_interfaces[i], NULL);
		ret = g_file_test (filename, G_FILE_TEST_EXISTS);
		if (ret)
			goto out;
		g_free (filename);
	}

	/* nothing found in the ordered list */
	filename = NULL;

	/* find any random ones */
	dir = g_dir_open (GSD_BACKLIGHT_HELPER_SYSFS_LOCATION, 0, &error);
	if (dir == NULL) {
		g_warning ("failed to find any devices: %s", error->message);
		g_error_free (error);
		goto out;
	}

	/* get first device if any */
	first_device = g_dir_read_name (dir);
	if (first_device != NULL) {
		filename = g_build_filename (GSD_BACKLIGHT_HELPER_SYSFS_LOCATION,
					     first_device, NULL);
	}
out:
	if (dir != NULL)
		g_dir_close (dir);
	return filename;
}

static gboolean
gsd_backlight_helper_write (const gchar *filename, gint value, GError **error)
{
	gchar *text = NULL;
	gint retval;
	gint length;
	gint fd = -1;
	gboolean ret = TRUE;

	fd = open (filename, O_WRONLY);
	if (fd < 0) {
		ret = FALSE;
		g_set_error (error, 1, 0, "failed to open filename: %s", filename);
		goto out;
	}

	/* convert to text */
	text = g_strdup_printf ("%i", value);
	length = strlen (text);

	/* write to device file */
	retval = write (fd, text, length);
	if (retval != length) {
		ret = FALSE;
		g_set_error (error, 1, 0, "writing '%s' to %s failed", text, filename);
		goto out;
	}
out:
	if (fd >= 0)
		close (fd);
	g_free (text);
	return ret;
}

int
main (int argc, char *argv[])
{
	GOptionContext *context;
	gint uid;
	gint euid;
	guint retval = 0;
	const gchar *pkexec_uid_str;
	GError *error = NULL;
	gboolean ret = FALSE;
	gint set_brightness = -1;
	gboolean get_brightness = FALSE;
	gboolean get_max_brightness = FALSE;
	gchar *filename = NULL;
	gchar *filename_file = NULL;
	gchar *contents = NULL;

	const GOptionEntry options[] = {
		{ "set-brightness", '\0', 0, G_OPTION_ARG_INT, &set_brightness,
		   /* command line argument */
		  "Set the current brightness", NULL },
		{ "get-brightness", '\0', 0, G_OPTION_ARG_NONE, &get_brightness,
		   /* command line argument */
		  "Get the current brightness", NULL },
		{ "get-max-brightness", '\0', 0, G_OPTION_ARG_NONE, &get_max_brightness,
		   /* command line argument */
		  "Get the number of brightness levels supported", NULL },
		{ NULL}
	};

	/* setup type system */
	g_type_init ();

	context = g_option_context_new (NULL);
	g_option_context_set_summary (context, "GNOME Settings Daemon Backlight Helper");
	g_option_context_add_main_entries (context, options, NULL);
	g_option_context_parse (context, &argc, &argv, NULL);
	g_option_context_free (context);

#ifndef __linux__
	/* the g-s-d plugin should only call this helper on linux */
	g_critical ("Attempting to call gsb-backlight-helper on non-Linux");
	g_assert_not_reached ();
#endif

	/* no input */
	if (set_brightness == -1 && !get_brightness && !get_max_brightness) {
		g_print ("%s\n", "No valid option was specified");
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID;
		goto out;
	}

	/* find device */
	filename = gsd_backlight_helper_get_best_backlight ();
	if (filename == NULL) {
		g_print ("%s\n", "No backlights were found on your system");
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_INVALID_USER;
		goto out;
	}

	/* GetBrightness */
	if (get_brightness) {
		filename_file = g_build_filename (filename, "brightness", NULL);
		ret = g_file_get_contents (filename_file, &contents, NULL, &error);
		if (!ret) {
			g_print ("%s: %s\n",
				 "Could not get the value of the backlight",
				 error->message);
			g_error_free (error);
			retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID;
			goto out;
		}

		/* just print the contents to stdout */
		g_print ("%s", contents);
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_SUCCESS;
		goto out;
	}

	/* GetSteps */
	if (get_max_brightness) {
		filename_file = g_build_filename (filename, "max_brightness", NULL);
		ret = g_file_get_contents (filename_file, &contents, NULL, &error);
		if (!ret) {
			g_print ("%s: %s\n",
				 "Could not get the maximum value of the backlight",
				 error->message);
			g_error_free (error);
			retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID;
			goto out;
		}

		/* just print the contents to stdout */
		g_print ("%s", contents);
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_SUCCESS;
		goto out;
	}

	/* get calling process */
	uid = getuid ();
	euid = geteuid ();
	if (uid != 0 || euid != 0) {
		g_print ("%s\n",
			 "This program can only be used by the root user");
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID;
		goto out;
	}

	/* check we're not being spoofed */
	pkexec_uid_str = g_getenv ("PKEXEC_UID");
	if (pkexec_uid_str == NULL) {
		g_print ("%s\n",
			 "This program must only be run through pkexec");
		retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_INVALID_USER;
		goto out;
	}

	/* SetBrightness */
	if (set_brightness != -1) {
		filename_file = g_build_filename (filename, "brightness", NULL);
		ret = gsd_backlight_helper_write (filename_file, set_brightness, &error);
		if (!ret) {
			g_print ("%s: %s\n",
				 "Could not set the value of the backlight",
				 error->message);
			g_error_free (error);
			retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_ARGUMENTS_INVALID;
			goto out;
		}
	}

	/* success */
	retval = GSD_BACKLIGHT_HELPER_EXIT_CODE_SUCCESS;
out:
	g_free (filename);
	g_free (filename_file);
	g_free (contents);
	return retval;
}


Close and Save.

5) Surf to the gnome-settings-daemon directory through terminal e.g.

> cd ~/gnome-settings-daemon-3.4.1

Then run the following code:

> sudo apt-get install intltool
sudo apt-get build-dep gnome-settings-daemon
./configure
make

6) Now replace some files manually:

> sudo mv /usr/lib/gnome-settings-daemon/gsd-backlight-helper /usr/lib/gnome-settings-daemon/gsd-backlight-helper.old
cd ~/gnome-settings-daemon-3.4.1/plugins/power/
sudo cp gsd-backlight-helper /usr/lib/gnome-settings-daemon/.

7) :popcorn:

---

### Post by squee on 2012-04-27
I have a different laptop but I found that I can only control the screen brightness using a command

sudo setpci -s 00:02.0 F4.B=XX    where XX is the the hex code for brightness level. 00 = black ff=brightest.

---

### Post by rfictus on 2012-04-28
Thx for the addition squee! The code in part 4.. is that Python ??

---

### Post by squee on 2012-04-29
> **rfictus said:**
> Thx for the addition squee! The code in part 4.. is that Python ??

no problem

part 4 looks like C or C++ but that's not my area.

---

### Post by adelani on 2012-05-06
Thanks [ Solved ]
I have sony Vaio VGN-FZ340E ( Ubuntu 12.04 )
Many Thanks

---

### Post by SeRpEnT86 on 2012-05-07
Hi, I've tried on my Sony VAIO S5M with ubuntu 12.04 and propertary Nvidia drivers but it doesn't work :sad:[-X:-x

---

### Post by rfictus on 2012-05-10
I think you need to run through the steps more carefully, are you sure each step was initiated?

---

### Post by SeRpEnT86 on 2012-05-12
Yes I'm sure, I've just tried another time but with the same results... It doesn't work!!:evil:

---

### Post by knopfra73 on 2012-05-14
In the above source code in c, just exchange the string "nv_backlight" with the string "nvidia_backlight" below it, so that  "nvidia_backlight" is the first element of the array. The reason is that you, as me, could have two folders under /sys/class/backlight, e.g.:
/sys/class/backlight$ ls
acpi_video0  nvidia_backlight

and the working one is nvidia_backlight

---

### Post by wentzr on 2012-05-16
I walked through these steps and so far have had no luck. All steps initiated correctly and completed w/o error.

Are these steps dm agnostic?? Im running lxde.. also ive a slight variation with the vaio model number, im on a vpccw13fx.

Hitting fn+f5/f6 slides a brightness slider HUD but no change in my screen's brightness.

No popcorn for me!! :(

EDIT: 

No this is not DE agnostic...  this fix does not work for LXDE. 

I can confirm however it does at least work here in KDE and should be good for Gnome and Unity

---

### Post by cher80 on 2012-05-21
[B][rfictus]("http://ubuntuforums.org/member.php?u=1605717")
[/B]thanks! works perfectly for me. As I understand you fixed this in source, then recompile and replace the lib . May be you attach the final gsd-backlight-helper so others can just replace it in libs?

---

### Post by androphi on 2012-05-26
My Laptop is VGN-FZ11S Sony Vaio

I searched for the solution all over the universe and here it is.

1000 THANKS
 
:guitar::lolflag: ;):-({|=

---

### Post by IntuitiveNipple on 2012-08-25
You can now avoid touching gnome-settings-daemon at all. I've added the module parameter "**type**" to 'nvidiabl' to enable users to change the backlight type from the default "*raw*".

gnome-settings-daemon looks for back-light devices in the following order:

1. firmware
2. platform
3. raw

If the system has a platform or firmware backlight driver (that doesn't work) then 'nvidiabl' would never get used.

By loading 'nvidiabl' with the "**type=firmware**" parameter gnome-settings-daemon will prefer it to most other backlight controllers in the system.

The code is currently in my github repository

[https://github.com/iam-TJ/nvidiabl/tree/issue-47](https://github.com/iam-TJ/nvidiabl/tree/issue-47)

but I've sent a pull request to Guillaume Zin so it is likely to be added to the primary 'nvidiabl' repository soon.

I'm also working on getting 'nvidiabl' added into the Ubuntu archive kernel packages.

```
 Issue 47: Add 'type' parameter to support gnome-settings-daemon

gnome-settings-daemon prefers backlight devices in the order:

firmware
platform
raw

By default 'nvidiabl' sets itself to 'raw'. Adding this module option allows the
user to configure the type so as to have nvidiabl chosen in preference to other
backlight drivers (such as ACPI platform drivers).

To use it, add the option "type=?" to the module options replacing '?' with one
of the types listed above. E.g:

options nvidiabl type=firmware

or:

sudo modprobe nvidiabl type=firmware

Signed-off-by: TJ <linux@iam.tj>
```

---

### Post by blume666 on 2012-10-23
Hey does anyone have a solution for the newest gnome-settings-daemon? I'm using a pre-alpha of elementaryOS. And with this solution it workes sometimes, but after a while the screen gets automatically brighter and the FN-keys doesn't work anymore. :(

---

### Post by muhammedsalihtk on 2013-04-06
i have similar problem..
i have SONY VAIO SVE15113EN...
there is no additinal graphic card in my laptop, only intel graphics hd 3000
please help me

---

