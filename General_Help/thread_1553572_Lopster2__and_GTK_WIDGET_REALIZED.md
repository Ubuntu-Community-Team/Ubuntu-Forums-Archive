---
title: "Lopster2  and GTK_WIDGET_REALIZED"
date: 2010-08-15
forum: General Help
---

### Post by user777777 on 2010-08-15
about lopster
[http://lopster.sourceforge.net/](http://lopster.sourceforge.net/)

The reason i want this new lopster2 is because of the OpenNap, soulseek and directconnect features. 

I Love the Lopster client, for downloading sharing files and so on it's a great program and now there is lopsterII that ive had running on Linux (fedora) last year, however ive tried compiling on the latest Ubuntu and it compiled but when i start it i get the following.



ubuntu@ubuntu:~$ lopster2
Starting lopster
XML        | registered 'core:string_lists' as '/home/ubuntu/.2lopster/string_lists.xml'
XML        | registered 'core:ui' as '/home/ubuntu/.2lopster/ui.xml'
PLUGIN     | adding to library path: /usr/local/lib/lopster
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_core.so.0.0.0'
DYNAMIC    | closing '/usr/local/lib/lopster/libgtk2_core.so.0.0.0'
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_core.so.0'
DYNAMIC    | closing '/usr/local/lib/lopster/libgtk2_core.so.0'
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_core.so'
DYNAMIC    | closing '/usr/local/lib/lopster/libgtk2_core.so'
UI         | new UI found: [Gtk+-2.0 - The GIMP Toolkit] /usr/local/lib/lopster/libgtk2_core.so
XML        | loading '/home/ubuntu/.2lopster/ui.xml'
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_core.so'
XML        | registered 'core:plugins' as '/home/ubuntu/.2lopster/plugins.xml'
PLUGIN     | searching for new plugins
PLUGIN     | new plugin /usr/local/lib/lopster/libplugin_nap.so.0.0.0 will be loaded by default
PLUGIN     | new plugin /usr/local/lib/lopster/libplugin_dc.so.0.0.0 will be loaded by default
PLUGIN     | new plugin /usr/local/lib/lopster/libplugin_slsk.so.0.0.0 will be loaded by default
PLUGIN     | attempting to load plugins
DYNAMIC    | opening '/usr/local/lib/lopster/libplugin_nap.so.0.0.0'
PLUGIN     | plugin 'OpenNap' will be loaded
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_nap.so'
DYNAMIC    | opening '/usr/local/lib/lopster/libplugin_dc.so.0.0.0'
PLUGIN     | plugin 'DirectConnect' will be loaded
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_dc.so'
DYNAMIC    | opening '/usr/local/lib/lopster/libplugin_slsk.so.0.0.0'
PLUGIN     | plugin 'Soulseek' will be loaded
DYNAMIC    | opening '/usr/local/lib/lopster/libgtk2_slsk.so'
MODULE     | Initializing modules...
MODULE     | initializing 'Dynamic Module'
MODULE     | initializing 'XML Module'
MODULE     | initializing 'Preferences Module'
XML        | registered 'core:prefs' as '/home/ubuntu/.2lopster/preferences.xml'
MODULE     | initializing 'String List Module'
MODULE     | initializing 'Base Module'
PREF       | registered value '/core/user/nick' : 'TestUser'
PREF       | registered value '/core/user/pass' : 'testpass'
PREF       | registered value '/core/user/description' : ''
PREF       | registered value '/core/user/picture' : ''
PREF       | registered value '/core/user/away' : 'no'
PREF       | registered value '/core/user/away_message' : ''
PREF       | registered value '/core/line/type' : '0'
PREF       | registered value '/core/line/speed' : '0'
PREF       | registered value '/core/desktop/browser' : 'gnome-open'
PREF       | registered value '/core/desktop/email' : 'evolution'
MODULE     | initializing 'Search Module'
ATTR       | registered attribute 'Size' for domain 'pattern'
ATTR       | registered attribute 'Bitrate' for domain 'pattern'
ATTR       | registered attribute 'Frequency' for domain 'pattern'
ATTR       | registered attribute 'Duration' for domain 'pattern'
MODULE     | initializing 'Load Module'
MODULE     | initializing 'Port Module'
MODULE     | initializing 'Limit Module'
MODULE     | initializing 'LSocket Module'
PREF       | registered value '/core/local/force_ip' : 'no'
PREF       | registered value '/core/local/ip' : '0.0.0.0'
MODULE     | initializing 'BSocket Module'
MODULE     | initializing 'TSocket Module'
MODULE     | initializing 'Download Module'
XML        | registered 'core:downloads' as '/home/ubuntu/.2lopster/downloads.xml'
PREF       | registered value '/core/download/limit' : '10'
PREF       | registered value '/core/download/limit_per_user' : '1'
PREF       | registered value '/core/download/limit_per_file' : '10'
PREF       | registered value '/core/download/bandlimit' : '204800'
PREF       | registered value '/core/path/incomplete' : ''
MODULE     | initializing 'Upload Module'
PREF       | registered value '/core/upload/limit' : '3'
PREF       | registered value '/core/upload/limit_per_user' : '1'
PREF       | registered value '/core/upload/bandlimit' : '14336'
MODULE     | initializing 'Thread Module'
MODULE     | initializing 'MType Module'
XML        | registered 'core:mtypes' as '/home/ubuntu/.2lopster/media.xml'
MODULE     | initializing 'Library Module'
XML        | registered 'core:library' as '/home/ubuntu/.2lopster/share/shared.xml'
PREF       | registered value '/core/lib/mark_val' : '0'
PREF       | registered value '/core/lib/current' : 'shared.xml'
ATTR       | registered attribute 'Bitrate' for domain 'file'
ATTR       | registered attribute 'Frequency' for domain 'file'
ATTR       | registered attribute 'VBR' for domain 'file'
ATTR       | registered attribute 'Duration' for domain 'file'
ATTR       | registered attribute 'Title' for domain 'file'
ATTR       | registered attribute 'Artist' for domain 'file'
ATTR       | registered attribute 'Album' for domain 'file'
ATTR       | registered attribute 'Year' for domain 'file'
LIB        | registered new file processing function 'file_parse_mp3'
MODULE     | initializing 'Legacy Module'
MODULE     | initializing 'User Interface Module'
XML        | registered 'ui:core:settings' as '/home/ubuntu/.2lopster/gtk2/settings.xml'
XML        | registered 'ui:core:styles' as '/home/ubuntu/.2lopster/gtk2/styles.xml'
XML        | registered 'ui:core:layout' as '/home/ubuntu/.2lopster/gtk2/layout.xml'
GTK_STYLE  | registerd style 'bandwidth:color'
GTK_STYLE  | registerd style 'filetree:recent'
GTK_STYLE  | registerd style 'search:available'
GTK_STYLE  | registerd style 'network:entry:online'
GTK_STYLE  | registerd style 'transfer:bar'
MODULE     | initializing 'Timer Module'
MODULE     | initializing 'Command Module'
MODULE     | initializing 'Chat Module'
PREF       | registered value '/core/chat/hide' : '0'
PREF       | registered value '/core/chat/pipe' : '3'
PREF       | registered value '/core/chat/timestamp' : '2'
PREF       | registered value '/core/chat/auto_rejoin' : 'yes'
PREF       | registered value '/core/chat/colored_nicks' : '2'
PREF       | registered value '/core/chat/prefix/server' : '*'
PREF       | registered value '/core/chat/prefix/client' : '#'
PREF       | registered value '/core/chat/prefix/join' : '>'
PREF       | registered value '/core/chat/prefix/part' : '<'
PREF       | registered value '/core/chat/prefix/text' : ' '
MODULE     | initializing 'Napster Command Module'
MODULE     | initializing 'User Module'
MODULE     | initializing 'Buddy Module'
XML        | registered 'core:buddies' as '/home/ubuntu/.2lopster/buddy.xml'
MODULE     | initializing 'Resolve Module'
MODULE     | initializing 'Listen Module'
PREF       | registered value '/core/listen/range' : '1025-65535'
PREF       | registered value '/core/listen/firewalled' : 'no'
MODULE     | initializing 'Nap Network Module'
XML        | registered 'nap:serverlist' as '/home/ubuntu/.2lopster/nap/servers.xml'
PREF       | registered value '/nap/username' : ''
PREF       | registered value '/nap/password' : ''
PREF       | registered value '/nap/listen/port' : '6699'
MODULE     | initializing 'Napster User Module'
MODULE     | initializing 'Nap Hotlist Module'
ATTR       | registered attribute 'NapNick' for domain 'buddy'
MODULE     | initializing 'Nap User Interface Module'
MODULE     | initializing 'Nap Search Module'
ATTR       | registered attribute 'NapSpeed' for domain 'pattern'
MODULE     | initializing 'Nap Download Module'
MODULE     | initializing 'Browse Module'
MODULE     | initializing 'Napster Module'
PREF       | registered value '/nap/chat/channels/min' : '5'
PREF       | registered value '/nap/chat/channels/max' : '0'
PREF       | registered value '/nap/usermode' : '4194303'
PREF       | registered value '/nap/charset' : ''
MODULE     | initializing 'Dc User Interface Module'
MODULE     | initializing 'Dc Command Module'
MODULE     | initializing 'Dc User Module'
MODULE     | initializing 'Dc Hotlist Module'
ATTR       | registered attribute 'DcNick' for domain 'buddy'
MODULE     | initializing 'Udp Module'
MODULE     | initializing 'LibSearch Module'
MODULE     | initializing 'Dc Search Module'
ATTR       | registered attribute 'urn:tree:tiger' for domain 'pattern'
MODULE     | initializing 'Dc Hub Module'
XML        | registered 'dc:hublist' as '/home/ubuntu/.2lopster/dc/hub_list.xml'
PREF       | registered value '/dc/username' : ''
PREF       | registered value '/dc/password' : ''
PREF       | registered value '/dc/listen/udp_port' : '9000'
PREF       | registered value '/dc/listen/tcp_port' : '4111'
PREF       | registered value '/dc/chat/autojoin' : 'no'
MODULE     | initializing 'Dc Share Module'
MODULE     | initializing 'Dc Download Module'
MODULE     | initializing 'Dc browse Module'
MODULE     | initializing 'DirectConnect Module'
ATTR       | registered attribute 'urn:tree:tiger' for domain 'file'
LIB        | registered new file processing function 'file_hash_tth'
MODULE     | initializing 'Soulseek Command Module'
MODULE     | initializing 'Slsk User Interface Module'
MODULE     | initializing 'Slsk Netlist Module'
PREF       | registered value '/slsk/listen/port' : '2234'
PREF       | registered value '/slsk/username' : ''
PREF       | registered value '/slsk/password' : ''
PREF       | registered value '/slsk/server/address' : 'server.slsknet.org'
PREF       | registered value '/slsk/server/port' : '2240'
MODULE     | initializing 'Soulseek User Module'
MODULE     | initializing 'Slsk Hotlist Module'
ATTR       | registered attribute 'SlskNick' for domain 'buddy'
MODULE     | initializing 'Slsk Download Module'
XML        | registered 'slsk:pots' as '/home/ubuntu/.2lopster/slsk/potentials.xml'
MODULE     | initializing 'Slsk Search Module'
MODULE     | initializing 'Slsk Netlist Module'
XML        | registered 'slsk:channel:charset' as '/home/ubuntu/.2lopster/slsk/channel.xml'
MODULE     | initializing 'Soulseek Module'
PREF       | registered value '/slsk/protocol' : '181'
PREF       | registered value '/slsk/charset' : 'WINDOWS-1252'
MODULE     | initializing 'Plugin Module'
PREF       | registered value '/version/Core' : '0'
PREF       | registered value '/version/Nap' : '0'
PREF       | registered value '/version/DC' : '0'
PREF       | registered value '/version/Slsk' : '0'
MODULE     | initializing 'Http Module'
PREF       | registered value '/core/http/proxy/enabled' : 'no'
PREF       | registered value '/core/http/proxy/host' : ''
PREF       | registered value '/core/http/proxy/port' : '0'
MODULE     | initializing 'Web Module'
PREF       | registered value '/core/web/port' : '1212'
PREF       | registered value '/core/web/active' : 'no'
PREF       | registered value '/core/web/username' : ''
PREF       | registered value '/core/web/password' : ''
PREF       | registered value '/core/web/resource_path' : '/usr/local/share/lopster/html'
MODULE     | initializing 'Global Command Module'
COMMAND    | registered new command [Core] 'plugin'
COMMAND    | registered new command [Core] 'help'
COMMAND    | registered new command [Core] 'pref'
COMMAND    | registered new command [Core] 'exec'
MODULE     | initializing 'Lopster Module'
MODULE     | Running modules...
MODULE     | running 'Dynamic Module'
MODULE     | running 'XML Module'
MODULE     | running 'Preferences Module'
MODULE     | running 'String List Module'
MODULE     | running 'Base Module'
MODULE     | running 'Search Module'
XML        | registered 'core:patterns' as '/home/ubuntu/.2lopster/search_pattern.xml'
MODULE     | running 'Load Module'
MODULE     | running 'Port Module'
PORT       | added allowed port range  1025 - 65535
MODULE     | running 'Limit Module'
MODULE     | running 'LSocket Module'
MODULE     | running 'BSocket Module'
MODULE     | running 'TSocket Module'
MODULE     | running 'Download Module'
MODULE     | running 'Upload Module'
MODULE     | running 'Thread Module'
MODULE     | running 'MType Module'
MODULE     | running 'Library Module'
MODULE     | running 'Legacy Module'
MODULE     | running 'User Interface Module'
lopster2: symbol lookup error: /usr/local/lib/lopster/libgtk2_core.so: undefined symbol: GTK_WIDGET_REALIZED
ubuntu@ubuntu:~$ 

Iv'e heard of other people with the  GTK_WIDGET_REALIZED problem, but not been able to solve it.

If anyone wants to join me on getting this program up and running, go ahead :)

Note: this client is hardly being updated now but there are hardly any multisource clients out there.

---

### Post by Corin-EU on 2011-03-20
The problem is that GTK_WIDGET_REALIZED is not defined as either a function or macro from a CFLAGS define from the Makefile or within the source code its-self.

And there are a number of other similar tokens which have not been defined either eg GTK_WIDGET_SENSITIVE.

This is because the flag GTK_DISABLE_DEPRECATED has been set in all of the Makefiles.

Therefore what you need to do, is go to your build directory and edit the
file configure.ac and change line 238 from

GTK2_CFLAGS="$GTK2_CFLAGS -DGTK_DISABLE_DEPRECATED"

to

GTK2_CFLAGS="$GTK2_CFLAGS"

ie remove the GTK_DISABLE_DEPRECATED flag.

Then you have to recreate the configure script by running the Bourne shell script

autogen.sh

found in the same top level directory of the build tree.

Then run configure again with your --prefix set as appropriate and any other custom settings you have chosen, followed by make and make install as normal.

Your newly built lopster2 should then run without complaining about undefined symbols in the libgtk2_core.so shared library.

---

