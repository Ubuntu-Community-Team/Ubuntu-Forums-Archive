---
title: "gnome-tweak-tool (Unknown extension error) BUG and FIX"
date: 2011-11-02
forum: General Help
---

### Post by phDaemon on 2011-11-02
So, i noticed that after enabling the ricotz PPA a lot of gnome-shell extensions would no longer work.

So i did a little bit of digging and found the following

in /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py the following code has been added to "report errors to the user" (Lines 20-39)
```

       self._shell = shell
        state = ext.get("state")

        sw = Gtk.Switch()
        sw.set_active(self._shell.extension_is_active(state, ext["uuid"]))
        sw.connect('notify::active', self._on_extension_toggled, ext["uuid"])

        warning = None
        sensitive = False
        if state == GnomeShell.EXTENSION_STATE["ENABLED"] or \
           state == GnomeShell.EXTENSION_STATE["DISABLED"]:
            sensitive = True
        elif state == GnomeShell.EXTENSION_STATE["ERROR"]:
            warning = _("Error loading extension")
        elif state == GnomeShell.EXTENSION_STATE["OUT_OF_DATE"]:
            warning = _("Extension does not support shell version")
        else:
            warning = _("Unknown extension error")
            logging.critical(warning)
        sw.set_sensitive(sensitive)

```

I noticed some of the extensions i was using were reporting "Unknown extension error"

So I logged the state, and found that the state number was 6.

I went into /usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py

and found this (lines 48-61):
```

class GnomeShell:

    EXTENSION_STATE = {
        "ENABLED"       :   1,
        "DISABLED"      :   2,
        "ERROR"         :   3,
        "OUT_OF_DATE"   :   4
    }

    EXTENSION_TYPE = {
        "SYSTEM"        :   1,
        "PER_USER"      :   2
    }

```

then i replaced it with this:
```

class GnomeShell:

    EXTENSION_STATE = {
        "ENABLED"       :   1,
        "DISABLED"      :   2,
        "ERROR"         :   3,
        "OUT_OF_DATE"   :   4,
        "DISABLED"      :   6
    }

    EXTENSION_TYPE = {
        "SYSTEM"        :   1,
        "PER_USER"      :   2
    }

```

Now all my extensions that did NOT work, seem to be working again.

Another error that i found in this version of gnome-tweak-tool was that it was looking for a "Summary" in all the schemas.

so in /usr/lib/python2.7/dist-packages/gtweak/gsettings.py(lines 44-52)
I changed
```

                        #summary is compulsory, description is optional
                        summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                        try:
                            description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }

```

TO THIS:

```

                        #summary is compulsory, description is optional
                        try:
                            summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                            description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
                            summary = "No Summary"
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }

```

Now i get no ERRORS at all when i'm using gnome-tweak-tool and all the extensions work as they should.

Hopefully this helps out any noobies looking for a fix.

I also contacted ricotz to see when this stuff will be fixed.

---

### Post by phDaemon on 2011-11-02
MODS: Please move this over to the Desktop environment area (Where it probably should be!), and sorry for my mistake of posting it here!!

---

### Post by Pauldb on 2011-11-03
DUDE Thank for the tip, it worked great for me !

I've been having this issue for a while without finding an answer, THANK YOU !

---

### Post by phDaemon on 2011-11-03
YW :)

I knew some other ppl out there must have been having this issue as well! lol, i couldnt find an answer anywhere so... decided to fix it myself :)

---

### Post by soro2005 on 2011-11-03
Thanks from here as well!!

---

### Post by fidro on 2011-11-07
I tried this but gnome tweak tool won't start anymore at all. :(
When I reinstall it, problem is back again.

more about my problem:

[http://askubuntu.com/questions/76072/cant-enable-gnome-shell-extensions]("http://askubuntu.com/questions/76072/cant-enable-gnome-shell-extensions")

---

### Post by phDaemon on 2011-11-07
Post the contents of

/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py

/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py

/usr/lib/python2.7/dist-packages/gtweak/gsettings.py

using code tags in here.

Then i may be able to help :)

---

### Post by fidro on 2011-11-07
/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py

```
import os.path
import zipfile
import tempfile
import logging
import json

from gi.repository import Gtk
from gi.repository import GLib

from gtweak.utils import extract_zip_file
from gtweak.gshellwrapper import GnomeShell, GnomeShellFactory
from gtweak.tweakmodel import Tweak, TweakGroup
from gtweak.widgets import ZipFileChooserButton, build_label_beside_widget, build_horizontal_sizegroup

class _ShellExtensionTweak(Tweak):

    def __init__(self, shell, ext, **options):
        Tweak.__init__(self, ext["name"], ext.get("description",""), **options)

        self._shell = shell
        state = ext.get("state")

        sw = Gtk.Switch()
        sw.set_active(self._shell.extension_is_active(state, ext["uuid"]))
        sw.connect('notify::active', self._on_extension_toggled, ext["uuid"])

        warning = None
        sensitive = False
        if state == GnomeShell.EXTENSION_STATE["ENABLED"] or \
           state == GnomeShell.EXTENSION_STATE["DISABLED"]:
            sensitive = True
        elif state == GnomeShell.EXTENSION_STATE["ERROR"]:
            warning = _("Error loading extension")
        elif state == GnomeShell.EXTENSION_STATE["OUT_OF_DATE"]:
            warning = _("Extension does not support shell version")
        else:
            warning = _("Unknown extension error")
            logging.critical(warning)
        sw.set_sensitive(sensitive)

        self.widget = build_label_beside_widget(
                        _("%s Extension") % ext["name"],
                        sw,
                        warning=warning)
        self.widget_for_size_group = sw

    def _on_extension_toggled(self, sw, active, uuid):
        if not sw.get_active():
            self._shell.disable_extension(uuid)
        else:
            self._shell.enable_extension(uuid)

        if self._shell.EXTENSION_NEED_RESTART:
            self.notify_action_required(
                _("The shell must be restarted for changes to take effect"),
                _("Restart"),
                self._shell.restart)

class _ShellExtensionInstallerTweak(Tweak):

    EXTENSION_DIR = os.path.join(GLib.get_user_data_dir(), "gnome-shell", "extensions")

    def __init__(self, shell, **options):
        Tweak.__init__(self, _("Install Shell Extension"), "", **options)

        self._shell = shell

        chooser = ZipFileChooserButton(_("Select an extension"))
        chooser.connect("file-set", self._on_file_set)

        self.widget = build_label_beside_widget(self.name, chooser)
        self.widget_for_size_group = chooser

    def _on_file_set(self, chooser):
        f = chooser.get_filename()

        with zipfile.ZipFile(f, 'r') as z:
            try:
                fragment = ()
                file_extension = None
                file_metadata = None
                for n in z.namelist():
                    if n.endswith("metadata.json"):
                        fragment = n.split("/")[0:-1]
                        file_metadata = n
                    if n.endswith("extension.js"):
                        if file_extension:
                            raise Exception("Only one extension per zip file")
                        file_extension = n

                if not file_metadata:
                    raise Exception("Could not find metadata.json")
                if not file_extension:
                    raise Exception("Could not find extension.js")

                #extract the extension uuid
                extension_uuid = None
                tmp = tempfile.mkdtemp()
                z.extract(file_metadata, tmp)
                with open(os.path.join(tmp, file_metadata)) as f:
                    try:
                        extension_uuid = json.load(f)["uuid"]
                    except:
                        logging.warning("Invalid extension format", exc_info=True)

                ok = False
                if extension_uuid:
                    ok, updated = extract_zip_file(
                                    z,
                                    "/".join(fragment),
                                    os.path.join(self.EXTENSION_DIR, extension_uuid))

                if ok:
                    if updated:
                        verb = _("%s extension updated successfully") % extension_uuid
                    else:
                        verb = _("%s extension installed successfully") % extension_uuid

                    self.notify_action_required(
                        verb,
                        _("Restart"),
                        self._shell.restart)

                else:
                    self.notify_error(_("Error installing extension"))


            except:
                #does not look like a valid theme
                self.notify_error(_("Invalid extension"))
                logging.warning("Error parsing theme zip", exc_info=True)

        #set button back to default state
        chooser.unselect_all()

class ShellExtensionTweakGroup(TweakGroup):
    def __init__(self):
        TweakGroup.__init__(self, _("Shell Extensions"))

        extension_tweaks = []
        sg = build_horizontal_sizegroup()

        #check the shell is running
        try:
            shell = GnomeShellFactory().get_shell()

            #add the extension installer
            extension_tweaks.append(
                _ShellExtensionInstallerTweak(shell, size_group=sg))

            try:
                #add a tweak for each installed extension
                for extension in shell.list_extensions().values():
                    try:
                        extension_tweaks.append(
                            _ShellExtensionTweak(shell, extension, size_group=sg))
                    except:
                        logging.warning("Invalid extension", exc_info=True)
            except:
                logging.warning("Error listing extensions", exc_info=True)
        except:
            logging.warning("Error detecting shell", exc_info=True)

        self.set_tweaks(*extension_tweaks)

TWEAK_GROUPS = (
        ShellExtensionTweakGroup(),
)
```

/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py

```
# This file is part of gnome-tweak-tool.
#
# Copyright (c) 2011 John Stowers
#
# gnome-tweak-tool is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# gnome-tweak-tool is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with gnome-tweak-tool.  If not, see <http://www.gnu.org/licenses/>.

import os.path
import json
import logging

from gi.repository import Gio
from gi.repository import GLib

import gtweak.utils
from gtweak.gsettings import GSettingsSetting

class _ShellProxy:
    def __init__(self):
        d = Gio.bus_get_sync(Gio.BusType.SESSION, None)
        self.proxy = Gio.DBusProxy.new_sync(
                            d, 0, None,
                            'org.gnome.Shell',
                            '/org/gnome/Shell',
                            'org.gnome.Shell',
                            None)

    def execute_js(self, js):
        result, output = self.proxy.Eval('(s)', js)
        if not result:
            raise Exception(output)
        return output

    @property
    def version(self):
        return json.loads(self.execute_js('const Config = imports.misc.config; Config.PACKAGE_VERSION'))

class GnomeShell:

    EXTENSION_STATE = {
        "ENABLED"       :   1,
        "DISABLED"      :   2,
        "ERROR"         :   3,
        "OUT_OF_DATE"   :   4,
        "DISABLED"      :   6
    }

    EXTENSION_TYPE = {
        "SYSTEM"        :   1,
        "PER_USER"      :   2
    }

    DATA_DIR = os.path.join(GLib.get_user_data_dir(), "gnome-shell")

    def __init__(self, shellproxy, shellsettings):
        self._proxy = shellproxy
        self._settings = shellsettings

    def restart(self):
        self._proxy.execute_js('global.reexec_self();')

    def reload_theme(self):
        self._proxy.execute_js('const Main = imports.ui.main; Main.loadTheme();')

    @property
    def version(self):
        return self._proxy.version

class GnomeShell30(GnomeShell):

    EXTENSION_DISABLED_KEY = "disabled-extensions"
    EXTENSION_NEED_RESTART = True

    def __init__(self, *args, **kwargs):
        GnomeShell.__init__(self, *args, **kwargs)

    def list_extensions(self):
        out = self._proxy.execute_js('const ExtensionSystem = imports.ui.extensionSystem; ExtensionSystem.extensionMeta')
        return json.loads(out)

    def extension_is_active(self, state, uuid):
        return state == GnomeShell.EXTENSION_STATE["ENABLED"] and \
                not self._settings.setting_is_in_list(self.EXTENSION_DISABLED_KEY, uuid)

    def enable_extension(self, uuid):
        self._settings.setting_remove_from_list(self.EXTENSION_DISABLED_KEY, uuid)

    def disable_extension(self, uuid):
        self._settings.setting_add_to_list(self.EXTENSION_DISABLED_KEY, uuid)

class GnomeShell32(GnomeShell):

    EXTENSION_ENABLED_KEY = "enabled-extensions"
    EXTENSION_NEED_RESTART = False

    def list_extensions(self):
        return self._proxy.proxy.ListExtensions()

    def extension_is_active(self, state, uuid):
        return state == GnomeShell.EXTENSION_STATE["ENABLED"] and \
                self._settings.setting_is_in_list(self.EXTENSION_ENABLED_KEY, uuid)

    def enable_extension(self, uuid):
        self._settings.setting_add_to_list(self.EXTENSION_ENABLED_KEY, uuid)

    def disable_extension(self, uuid):
        self._settings.setting_remove_from_list(self.EXTENSION_ENABLED_KEY, uuid)

@gtweak.utils.singleton
class GnomeShellFactory:
    def __init__(self):
        proxy = _ShellProxy()
        settings = GSettingsSetting("org.gnome.shell")
        v = map(int,proxy.version.split("."))

        if v >= [3,1,4]:
            self.shell = GnomeShell32(proxy, settings)
        else:
            self.shell = GnomeShell30(proxy, settings)

        logging.debug("Shell version: %s", str(v))

    def get_shell(self):
        return self.shell

if __name__ == "__main__":
    gtweak.GSETTINGS_SCHEMA_DIR = "/usr/share/glib-2.0/schemas/"

    s = GnomeShellFactory().get_shell()
    print "Shell Version: %s" % s.version
    print s.list_extensions()

    print s == GnomeShellFactory().get_shell()
```

/usr/lib/python2.7/dist-packages/gtweak/gsettings.py

```
# This file is part of gnome-tweak-tool.
#
# Copyright (c) 2011 John Stowers
#
# gnome-tweak-tool is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# gnome-tweak-tool is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with gnome-tweak-tool.  If not, see <http://www.gnu.org/licenses/>.

import logging
import os.path
import xml.dom.minidom

import gtweak

from gi.repository import Gio, GLib

class _GSettingsSchema:
    def __init__(self, schema_name, schema_dir=None, schema_filename=None, **options):
        if not schema_dir:
            schema_dir = gtweak.GSETTINGS_SCHEMA_DIR
        if not schema_filename:
            schema_filename = schema_name + ".gschema.xml"

        schema_path = os.path.join(schema_dir, schema_filename)
        assert(os.path.exists(schema_path))

        self._schema_name = schema_name
        self._schema = {}

        try:
            dom = xml.dom.minidom.parse(schema_path)
            for schema in dom.getElementsByTagName("schema"):
                if schema_name == schema.getAttribute("id"):
                    for key in schema.getElementsByTagName("key"):
                        #summary is compulsory, description is optional
			try:
                        summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                        description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
			    summary = "No Summary"
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }
        except:
            logging.critical("Error parsing schema %s (%s)" % (schema_name, schema_path), exc_info=True)

    def __repr__(self):
        return "<gtweak.gsettings._GSettingsSchema: %s>" % self._schema_name

_SCHEMA_CACHE = {}

class GSettingsSetting(Gio.Settings):
    def __init__(self, schema_name, **options):
        Gio.Settings.__init__(self, schema_name)
        if schema_name not in _SCHEMA_CACHE:
            _SCHEMA_CACHE[schema_name] = _GSettingsSchema(schema_name, **options)
            logging.debug("Caching gsettings: %s" % _SCHEMA_CACHE[schema_name])

        self._schema = _SCHEMA_CACHE[schema_name]

        if gtweak.VERBOSE:
            self.connect("changed", self._on_changed)

    def _on_changed(self, settings, key_name):
        print "Change: %s %s -> %s" % (self.props.schema, key_name, self[key_name])

    def _setting_check_is_list(self, key):
        variant = Gio.Settings.get_value(self, key)
        return variant.get_type_string() == "as"

    def schema_get_summary(self, key):
        return self._schema._schema[key]["summary"]
        
    def schema_get_description(self, key):
        return self._schema._schema[key]["description"]

    def schema_get_all(self, key):
        return self._schema._schema[key]

    def setting_add_to_list(self, key, value):
        """ helper function, ensures value is present in the GSettingsList at key """
        assert self._setting_check_is_list(key)

        vals = self[key]
        if value not in vals:
            vals.append(value)
            self[key] = vals
            return True

    def setting_remove_from_list(self, key, value):
        """ helper function, removes value in the GSettingsList at key (if present)"""
        assert self._setting_check_is_list(key)

        vals = self[key]
        try:
            vals.remove(value)
            self[key] = vals
            return True
        except ValueError:
            #not present
            pass

    def setting_is_in_list(self, key, value):
        assert self._setting_check_is_list(key)
        return value in self[key]

if __name__ == "__main__":
    gtweak.GSETTINGS_SCHEMA_DIR = "/usr/share/glib-2.0/schemas/"

    key = "draw-background"
    s = GSettingsSetting("org.gnome.desktop.background")
    print s.schema_get_summary(key), s.schema_get_description(key)

    key = "disabled-extensions"
    s = GSettingsSetting("org.gnome.shell")
    assert s.setting_add_to_list(key, "foo")
    assert s.setting_remove_from_list(key, "foo")
    assert not s.setting_remove_from_list(key, "foo")
```

P.S. I edited files (from your posts above) with command: $sudo gedit ...
I don't know if that is right, please notice that I'm great noob for linux, been using windows since Win95.

---

### Post by phDaemon on 2011-11-07
Python is pretty strict with tabbing (or syntax in general) so

replace your /usr/lib/python2.7/dist-packages/gtweak/gsettings.py

completely with this one:

```


# This file is part of gnome-tweak-tool.
#
# Copyright (c) 2011 John Stowers
#
# gnome-tweak-tool is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# gnome-tweak-tool is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with gnome-tweak-tool.  If not, see <http://www.gnu.org/licenses/>.

import logging
import os.path
import xml.dom.minidom

import gtweak

from gi.repository import Gio, GLib

class _GSettingsSchema:
    def __init__(self, schema_name, schema_dir=None, schema_filename=None, **options):
        if not schema_dir:
            schema_dir = gtweak.GSETTINGS_SCHEMA_DIR
        if not schema_filename:
            schema_filename = schema_name + ".gschema.xml"

        schema_path = os.path.join(schema_dir, schema_filename)
        assert(os.path.exists(schema_path))

        self._schema_name = schema_name
        self._schema = {}

        try:
            dom = xml.dom.minidom.parse(schema_path)
            for schema in dom.getElementsByTagName("schema"):
                if schema_name == schema.getAttribute("id"):
                    for key in schema.getElementsByTagName("key"):
                        #summary is compulsory, description is optional
                        try:
                            summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                            description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
                            summary = "No Summary"
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }
        except:
            logging.critical("Error parsing schema %s (%s)" % (schema_name, schema_path), exc_info=True)

    def __repr__(self):
        return "<gtweak.gsettings._GSettingsSchema: %s>" % self._schema_name

_SCHEMA_CACHE = {}

class GSettingsSetting(Gio.Settings):
    def __init__(self, schema_name, **options):
        Gio.Settings.__init__(self, schema_name)
        if schema_name not in _SCHEMA_CACHE:
            _SCHEMA_CACHE[schema_name] = _GSettingsSchema(schema_name, **options)
            logging.debug("Caching gsettings: %s" % _SCHEMA_CACHE[schema_name])

        self._schema = _SCHEMA_CACHE[schema_name]

        if gtweak.VERBOSE:
            self.connect("changed", self._on_changed)

    def _on_changed(self, settings, key_name):
        print "Change: %s %s -> %s" % (self.props.schema, key_name, self[key_name])

    def _setting_check_is_list(self, key):
        variant = Gio.Settings.get_value(self, key)
        return variant.get_type_string() == "as"

    def schema_get_summary(self, key):
        return self._schema._schema[key]["summary"]
        
    def schema_get_description(self, key):
        return self._schema._schema[key]["description"]

    def schema_get_all(self, key):
        return self._schema._schema[key]

    def setting_add_to_list(self, key, value):
        """ helper function, ensures value is present in the GSettingsList at key """
        assert self._setting_check_is_list(key)

        vals = self[key]
        if value not in vals:
            vals.append(value)
            self[key] = vals
            return True

    def setting_remove_from_list(self, key, value):
        """ helper function, removes value in the GSettingsList at key (if present)"""
        assert self._setting_check_is_list(key)

        vals = self[key]
        try:
            vals.remove(value)
            self[key] = vals
            return True
        except ValueError:
            #not present
            pass

    def setting_is_in_list(self, key, value):
        assert self._setting_check_is_list(key)
        return value in self[key]

if __name__ == "__main__":
    gtweak.GSETTINGS_SCHEMA_DIR = "/usr/share/glib-2.0/schemas/"

    key = "draw-background"
    s = GSettingsSetting("org.gnome.desktop.background")
    print s.schema_get_summary(key), s.schema_get_description(key)

    key = "disabled-extensions"
    s = GSettingsSetting("org.gnome.shell")
    assert s.setting_add_to_list(key, "foo")
    assert s.setting_remove_from_list(key, "foo")
    assert not s.setting_remove_from_list(key, "foo")

```

Let me know if you still get the same errors

---

### Post by fidro on 2011-11-07
THANK YOU VERY MUCH!!!

sorry for caps lock
:D:D:D:D

---

### Post by phDaemon on 2011-11-07
You're welcome :)

---

### Post by Sekerob on 2011-11-07
Defenitely brought back 5-6 extensions or made them come alive after these changes. The only one that stayed in the Unknown extension error state was the "Application Menu Extension" which before had the little Gnome foot icon, left top. I like me classic menu when "dash", sorry, "activities type to search" has me lost for the right words to find/launch and app. Nothing so irritating as this constant calling it one thing in installations, but then naming it something else. Gnome Tweak is showing here as Advanced Settings to give one of a zillion possible examples. gconf-editor is installed per synaptic, but for the life of it, not getting activities find it.

---

### Post by phDaemon on 2011-11-07
In /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py

Find

```

            warning = _("Unknown extension error")
            logging.critical(warning)

```

Right AFTER ADD
```

            logging.critical(state)

```

Save. Re-open gnome-tweak-tool from a terminal, let me know what the output is.

---

### Post by bmbaker on 2011-11-08
Hi there thanks for this i was having the same problem and had been playing around with it for a while now,

your solution wks great :-)
perhaps you can pass it on to John Storkower :-)
thanks again

---

### Post by Orwell_T89 on 2011-11-12
> **phDaemon said:**
> So, i noticed that after enabling the ricotz PPA a lot of gnome-shell extensions would no longer work.

So i did a little bit of digging and found the following

in /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py the following code has been added to "report errors to the user" (Lines 20-39)
```

       self._shell = shell
        state = ext.get("state")

        sw = Gtk.Switch()
        sw.set_active(self._shell.extension_is_active(state, ext["uuid"]))
        sw.connect('notify::active', self._on_extension_toggled, ext["uuid"])

        warning = None
        sensitive = False
        if state == GnomeShell.EXTENSION_STATE["ENABLED"] or \
           state == GnomeShell.EXTENSION_STATE["DISABLED"]:
            sensitive = True
        elif state == GnomeShell.EXTENSION_STATE["ERROR"]:
            warning = _("Error loading extension")
        elif state == GnomeShell.EXTENSION_STATE["OUT_OF_DATE"]:
            warning = _("Extension does not support shell version")
        else:
            warning = _("Unknown extension error")
            logging.critical(warning)
        sw.set_sensitive(sensitive)

```I noticed some of the extensions i was using were reporting "Unknown extension error"

So I logged the state, and found that the state number was 6.

I went into /usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py

and found this (lines 48-61):
```

class GnomeShell:

    EXTENSION_STATE = {
        "ENABLED"       :   1,
        "DISABLED"      :   2,
        "ERROR"         :   3,
        "OUT_OF_DATE"   :   4
    }

    EXTENSION_TYPE = {
        "SYSTEM"        :   1,
        "PER_USER"      :   2
    }

```then i replaced it with this:
```

class GnomeShell:

    EXTENSION_STATE = {
        "ENABLED"       :   1,
        "DISABLED"      :   2,
        "ERROR"         :   3,
        "OUT_OF_DATE"   :   4,
        "DISABLED"      :   6
    }

    EXTENSION_TYPE = {
        "SYSTEM"        :   1,
        "PER_USER"      :   2
    }

```Now all my extensions that did NOT work, seem to be working again.

Another error that i found in this version of gnome-tweak-tool was that it was looking for a "Summary" in all the schemas.

so in /usr/lib/python2.7/dist-packages/gtweak/gsettings.py(lines 44-52)
I changed
```

                        #summary is compulsory, description is optional
                        summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                        try:
                            description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }

```TO THIS:

```

                        #summary is compulsory, description is optional
                        try:
                            summary = key.getElementsByTagName("summary")[0].childNodes[0].data
                            description = key.getElementsByTagName("description")[0].childNodes[0].data
                        except:
                            description = ""
                            summary = "No Summary"
                        self._schema[key.getAttribute("name")] = {
                                "summary"       :   summary,
                                "description"   :   description
                        }

```Now i get no ERRORS at all when i'm using gnome-tweak-tool and all the extensions work as they should.

Hopefully this helps out any noobies looking for a fix.

I also contacted ricotz to see when this stuff will be fixed.

Hi there, I'm really new to this, I recently installed gnome 3 on my ubuntu 11.10 and I am having the same problem in gnome-tweak-tool. I am receiving the unknown extension error for ALL my gnome shell extensions, I only found this out when I couldn't get the gnome-themeselector to work. It seems I cannot switch on an of the gnome shell components at all. I therefore am assuming it's this bug which is causing this, I want to ask how you logged the state to find a state number, could you give me some steps to do in order to accomplish this, for I have absolutely no idea.

---

### Post by phDaemon on 2011-11-13
I explained how to do it two posts before yours :)

---

### Post by phDaemon on 2011-11-13
BTW, to all:

There was another update to the gnome-tweak-tool which I'm currently getting these errors:

```

WARNING : Could not list shell extensions
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 62, in __init__
    extensions = self._shell.list_extensions()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 107, in list_extensions
    return self._proxy.proxy.ListExtensions()
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.gnome.gjs.JSError.TypeError: out is undefined
No schema known for `/desktop/gnome/shell/windows/button_layout'
No schema known for `/desktop/gnome/shell/windows/button_layout'
WARNING : Error listing extensions
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 153, in __init__
    for extension in shell.list_extensions().values():
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 107, in list_extensions
    return self._proxy.proxy.ListExtensions()
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.gnome.gjs.JSError.TypeError: out is undefined
No schema known for `/desktop/gnome/shell/windows/theme'
No schema known for `/desktop/gnome/shell/windows/theme'

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

Gtk-CRITICAL **: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed

```

I'm currently trying to figure out some fixes for these (just started actually about 5 minutes ago). The fixes here do NOT fix the errors I just posted, and seem to be related to this bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/863329](https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/863329)

So, while I try to figure out some work-around please go ahead and post post in that bug's launchpad. (Hopefully the devs will also fix these issues :/)

---

### Post by phDaemon on 2011-11-13
If anyone is interested you can follow my progress in that link i provided above.

---

### Post by nzjrs on 2011-11-20
ARGH.

Can someone please collate this and forward this bug upstream so I can commit a fix.

Thanks,

John (gnome-tweak-tool developer)

---

### Post by nzjrs on 2011-11-20
Possible fix on gnome-tweak-tool master. Please test

[https://bugzilla.gnome.org/show_bug.cgi?id=664387](https://bugzilla.gnome.org/show_bug.cgi?id=664387)

---

### Post by fabrixx on 2011-11-20
Sorry in Debian testing i have same problem but i not have:
```

EXTENSION_STATE = {         "ENABLED"       :   1,         "DISABLED"      :   2,         "ERROR"         :   3,         "OUT_OF_DATE"   :   4
```


I have only:
```
# This file is part of gnome-tweak-tool.
#
# Copyright (c) 2011 John Stowers
#
# gnome-tweak-tool is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# gnome-tweak-tool is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with gnome-tweak-tool.  If not, see <http://www.gnu.org/licenses/>.

import os.path
import json

from gi.repository import Gio
from gi.repository import GLib

class _ShellProxy:
    def __init__(self):
        d = Gio.bus_get_sync(Gio.BusType.SESSION, None)
        self._proxy = Gio.DBusProxy.new_sync(
                            d, 0, None,
                            'org.gnome.Shell',
                            '/org/gnome/Shell',
                            'org.gnome.Shell',
                            None)

    def execute_js(self, js):
        result, output = self._proxy.Eval('(s)', js)
        if not result:
            raise Exception(output)
        return output

class GnomeShell:

    DATA_DIR = os.path.join(GLib.get_user_data_dir(), "gnome-shell")

    def __init__(self):
        self._proxy = _ShellProxy()

    def restart(self):
        self._proxy.execute_js('global.reexec_self();')

    def reload_theme(self):
        self._proxy.execute_js('const Main = imports.ui.main; Main.loadTheme();')

    def list_extensions(self):
        out = self._proxy.execute_js('const ExtensionSystem = imports.ui.extensionSystem; ExtensionSystem.extensionMeta')
        return json.loads(out)

    def get_version(self):
        return json.loads(self._proxy.execute_js('const Config = imports.misc.config; Config.PACKAGE_VERSION'))

if __name__ == "__main__":
    s = GnomeShell()
    print s.list_extensions()
```

I need to change entire file?

---

### Post by phDaemon on 2011-11-21
> **nzjrs said:**
> Possible fix on gnome-tweak-tool master. Please test

[https://bugzilla.gnome.org/show_bug.cgi?id=664387](https://bugzilla.gnome.org/show_bug.cgi?id=664387)

Hey John!
Im pretty honored that you found this thread (Must be catching on!)

I was away on vacation but I'll for sure test that for ya!

Thanks,
Victor

---

### Post by phDaemon on 2011-11-21
I found two errors.
The first one is with the user-theme extension (its not reading the max version number)

In the file "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py" Line: 71

It reads
```

                    self._usertheme_extension_version = max(extensions[ShellThemeTweak.THEME_EXT_NAME]["shell-version"])

```

Hard-coding the max version works (so I'm assuming the expected setting in the the array is wrong).

```

                    self._usertheme_extension_version = "3.2.1"
                    #max(extensions[ShellThemeTweak.THEME_EXT_NAME]["shell-version"])

```

That made it work for me.

This is my user-theme extension metadata.json file
```

{
 "uuid": "user-theme@gnome-shell-extensions.gnome.org",
 "name": "User Themes",
 "description": "Load shell themes from user directory",
 "shell-version": [ "3.2.1", "3.2" ],
 "localedir": "/usr/share/locale",
 "original-authors": [ "john.stowers@gmail.com" ],
 "url": "http://git.gnome.org/gnome-shell-extensions"
}

```

The second is, Gnome-tweak-tool no longer lets me change the buttons for the windows. For that one, i could not find a fix, or an error. Everything seems fine in the file tweak_shell, where some of those things seem to be defined (Im not very familiar with all the gconf settings so...)

```

class ShowWindowButtons(GConfComboTweak):
    def __init__(self, **options):
        GConfComboTweak.__init__(self,
            "/desktop/gnome/shell/windows/button_layout",
            str,
            ((':close', 'Close Only'),
            (':minimize,close', 'Minimize and Close'),
            (':maximize,close', 'Maximize and Close'),
            (':minimize,maximize,close', 'All')),
            **options)

```

What I mean by this is, even if i have it set to show: maximize, minimize and close, it only shows close anyways. (After a reset, reboot, and any other kind of standard refreshing).

---

### Post by phDaemon on 2011-11-21
> **fabrixx said:**
> Sorry in Debian testing i have same problem but i not have:
```

EXTENSION_STATE = {         "ENABLED"       :   1,         "DISABLED"      :   2,         "ERROR"         :   3,         "OUT_OF_DATE"   :   4
```


I have only:
```
# This file is part of gnome-tweak-tool.
#
# Copyright (c) 2011 John Stowers
#
# gnome-tweak-tool is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# gnome-tweak-tool is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with gnome-tweak-tool.  If not, see <http://www.gnu.org/licenses/>.

import os.path
import json

from gi.repository import Gio
from gi.repository import GLib

class _ShellProxy:
    def __init__(self):
        d = Gio.bus_get_sync(Gio.BusType.SESSION, None)
        self._proxy = Gio.DBusProxy.new_sync(
                            d, 0, None,
                            'org.gnome.Shell',
                            '/org/gnome/Shell',
                            'org.gnome.Shell',
                            None)

    def execute_js(self, js):
        result, output = self._proxy.Eval('(s)', js)
        if not result:
            raise Exception(output)
        return output

class GnomeShell:

    DATA_DIR = os.path.join(GLib.get_user_data_dir(), "gnome-shell")

    def __init__(self):
        self._proxy = _ShellProxy()

    def restart(self):
        self._proxy.execute_js('global.reexec_self();')

    def reload_theme(self):
        self._proxy.execute_js('const Main = imports.ui.main; Main.loadTheme();')

    def list_extensions(self):
        out = self._proxy.execute_js('const ExtensionSystem = imports.ui.extensionSystem; ExtensionSystem.extensionMeta')
        return json.loads(out)

    def get_version(self):
        return json.loads(self._proxy.execute_js('const Config = imports.misc.config; Config.PACKAGE_VERSION'))

if __name__ == "__main__":
    s = GnomeShell()
    print s.list_extensions()
```

I need to change entire file?


Update to the latest version and almost everything should be fixed :) (Thanks john!)

---

### Post by fabrixx on 2011-11-21
Solved, not a bug og tewak tool but of my shell-extension

---

### Post by nzjrs on 2011-11-23
The theme change should be working in git master.

The window buttons will not (until I use the new gsettings schema)

Please continue any discussion in bugzilla - I dont want to monitor forums for bug reports.

John (gnome-tweak-tool developer)

---

### Post by Alfagulf on 2011-12-17
phDaemon,

I need your help,

I am getting "Error loading extension" in gnome-tweak in front of the "system-monitor Extension"!
I have "Gimmie Extension" loaded with no problem.

I am using Oneiric 64bit and gnome shell 3.2.1.

I modified the two files you mentioned in your initial post, but that did not fix the problem.

Let me know if you need any more information.

Thanks
AlfaGulf



Update: [Solved] Just as I finished writing this post, I had an idea!
I removed and purged both gnome-shell and gnome-tweak and then re-installed them again, and to my surprise, the problem was solved!! :)
Thanks any way.
AlfaGulf

---

### Post by bmacgill on 2012-03-06
This is great insight into the root cause, but I'm still chasing a working solution. After applying your suggested fix, GTT wouldn't start at all, dumping this out on traceback:

:-?
```
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 76, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 44, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 40, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 131, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_nautilus.py", line 21, in <module>
    from gtweak.utils import AutostartManager
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 24, in <module>
    from gtweak.gsettings import GSettingsSetting
  File "/usr/lib/python2.7/dist-packages/gtweak/gsettings.py", line 47
    try:
      ^
IndentationError: expected an indented block

```

I'll feedback results of complete replacement in a bit, see if that works out.
~bmac out

---

### Post by bmacgill on 2012-03-06
hmm... I'm a stooge, I've got everything back in operation after checking the thread:

[https://bugs.launchpad.net/ubuntu/+s...ol/+bug/863329]("https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/863329")

thanks for this, I'm back in stylin flavor!

---

