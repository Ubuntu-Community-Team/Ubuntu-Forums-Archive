---
title: "phpmyadmin not working (Karmic)"
date: 2009-10-30
forum: General Help
---

### Post by stef25 on 2009-10-30
I just installed Ubuntu and upgraded to the latest Karmic, then installed apache2, php, mysql - all fine. localhost loads with a "It works" message.

I'd now like to install phpmyadmin. I installed it via the Synaptic Package Manager but when I load [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I just see a list of files, below.

[DIR]	Parent Directory	 	 -
[ ]	apache.conf	19-Oct-2009 17:25 	879
[ ]	config-db.php	30-Oct-2009 13:20 	542
[ ]	config.footer.inc.php	19-Oct-2009 17:25 	168
[ ]	config.header.inc.php	19-Oct-2009 17:25 	168
[ ]	config.inc.php	19-Oct-2009 17:25 	3.6K
[ ]	htpasswd.setup	30-Oct-2009 12:55 	8
[ ]	lighttpd.conf	19-Oct-2009 17:25 	570
[DIR]	myadm/	30-Oct-2009 13:20 	-
[ ]	phpmyadmin.service	19-Oct-2009 

A colleague put some entries in the apache2 conf file to "map" the localhost/phpmyadmin url to the installation but this didn't work. I'm not sure what he did (added the myadm folder ...), maybe he screwed things up. Sorry to be vague about this ...

How can I get phpmyadmin to work?

---

### Post by Giblet5 on 2009-10-30
It works great here.

When you install Apache2, a dialog pops up asking which HTTP server you want to use; lighthttpd or Apache2.

What did you choose?

I would completely remove Apache2 and phpmyadmin, wipe out everything in /var/www/phpmyadmin, and delete my Apache config, then reinstall apache2 and phpmyadmin.

```
sudo apt-get remove apache2 phpmyadmin --purge
sudo rm -fr /var/www/phpmyadmin /etc/apache2
sudo apt-get install apache2 phpmyadmin
```

---

### Post by stef25 on 2009-10-30
Thanks for your reply!

I chose Apache2 as option.

Followed all your instructions, went smooth. Now when I visit localhost/phpmyadmin I again see a list of files:

[DIR]	Parent Directory	 	 -
[ ]	apache.conf	19-Oct-2009 17:25 	879
[ ]	config-db.php	30-Oct-2009 14:00 	548
[ ]	config.footer.inc.php	19-Oct-2009 17:25 	168
[ ]	config.header.inc.php	19-Oct-2009 17:25 	168
[ ]	config.inc.php	19-Oct-2009 17:25 	3.6K
[ ]	htpasswd.setup	30-Oct-2009 14:00 	8
[ ]	lighttpd.conf	19-Oct-2009 17:25 	570
[ ]	phpmyadmin.service	19-Oct-2009 17:25 	295 

How can I get to the GUI?

---

### Post by Giblet5 on 2009-10-30
You DO have mysql and php installed, right?

```
sudo apt-get install mysql-server php5 php5-cli php5-mcrypt php5-mysql
```

Then flush your browser cache (Tools -> Clear Private Data) and reload the page.

---

### Post by stef25 on 2009-10-30
Done, no change. Just a list of files. Seems to be that there should be alot more files in this directory, no?

stef@stef-laptop:~$ sudo apt-get install mysql-server php5 php5-cli php5-mcrypt php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
php5-mcrypt is already the newest version.
php5-mcrypt set to manually installed.
php5-mysql is already the newest version.
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5 php5-cli
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,508kB of archives.
After this operation, 5,415kB of additional disk space will be used.
Get:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) karmic/main php5 5.2.10.dfsg.1-2ubuntu6 [1,120B]
Get:2 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) karmic/main php5-cli 5.2.10.dfsg.1-2ubuntu6 [2,507kB]
Fetched 2,508kB in 2s (837kB/s)     
Selecting previously deselected package php5.
(Reading database ... 130372 files and directories currently installed.)
Unpacking php5 (from .../php5_5.2.10.dfsg.1-2ubuntu6_all.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.2.10.dfsg.1-2ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Setting up php5 (5.2.10.dfsg.1-2ubuntu6) ...
Setting up php5-cli (5.2.10.dfsg.1-2ubuntu6) ...

Creating config file /etc/php5/cli/php.ini with new version
update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode.

---

### Post by Giblet5 on 2009-10-30
Hmmm. The file layout has changed. It's spread out all over the place: ```
$ locate phpmyadmin
/etc/phpmyadmin
/etc/apache2/conf.d/phpmyadmin.conf
/etc/avahi/services/phpmyadmin.service
/etc/dbconfig-common/phpmyadmin.conf
/etc/phpmyadmin/apache.conf
/etc/phpmyadmin/config-db.php
/etc/phpmyadmin/config.footer.inc.php
/etc/phpmyadmin/config.header.inc.php
/etc/phpmyadmin/config.inc.php
/etc/phpmyadmin/htpasswd.setup
/etc/phpmyadmin/lighttpd.conf
/etc/phpmyadmin/phpmyadmin.service
/usr/share/phpmyadmin
/usr/share/dbconfig-common/data/phpmyadmin
/usr/share/dbconfig-common/data/phpmyadmin/install
/usr/share/dbconfig-common/data/phpmyadmin/install/mysql
/usr/share/doc/phpmyadmin
/usr/share/doc/phpmyadmin/Documentation.html
/usr/share/doc/phpmyadmin/Documentation.txt.gz
/usr/share/doc/phpmyadmin/README.Debian
/usr/share/doc/phpmyadmin/TODO.Debian
/usr/share/doc/phpmyadmin/changelog.Debian.gz
/usr/share/doc/phpmyadmin/changelog.gz
/usr/share/doc/phpmyadmin/copyright
/usr/share/doc/phpmyadmin/docs.css
/usr/share/doc/phpmyadmin/examples
/usr/share/doc/phpmyadmin/translators.html
/usr/share/doc/phpmyadmin/examples/config.manyhosts.inc.php
/usr/share/doc/phpmyadmin/examples/config.sample.inc.php
/usr/share/doc/phpmyadmin/examples/create_tables.sql.gz
/usr/share/doc/phpmyadmin/examples/signon.php
/usr/share/doc/phpmyadmin/examples/upgrade_tables_mysql_4_1_2+.sql.gz
/usr/share/phpmyadmin/Documentation.html
/usr/share/phpmyadmin/browse_foreigners.php
/usr/share/phpmyadmin/bs_change_mime_type.php
/usr/share/phpmyadmin/bs_disp_as_mime_type.php
/usr/share/phpmyadmin/bs_play_media.php
/usr/share/phpmyadmin/calendar.php
/usr/share/phpmyadmin/changelog.php
/usr/share/phpmyadmin/chk_rel.php
/usr/share/phpmyadmin/config.footer.inc.php
/usr/share/phpmyadmin/config.header.inc.php
/usr/share/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/config.sample.inc.php
/usr/share/phpmyadmin/db_create.php
/usr/share/phpmyadmin/db_datadict.php
/usr/share/phpmyadmin/db_export.php
/usr/share/phpmyadmin/db_import.php
/usr/share/phpmyadmin/db_operations.php
/usr/share/phpmyadmin/db_printview.php
/usr/share/phpmyadmin/db_qbe.php
/usr/share/phpmyadmin/db_search.php
/usr/share/phpmyadmin/db_sql.php
/usr/share/phpmyadmin/db_structure.php
/usr/share/phpmyadmin/docs.css
/usr/share/phpmyadmin/error.php
/usr/share/phpmyadmin/export.php
/usr/share/phpmyadmin/favicon.ico
/usr/share/phpmyadmin/import.php
/usr/share/phpmyadmin/index.php
/usr/share/phpmyadmin/js
/usr/share/phpmyadmin/lang
/usr/share/phpmyadmin/libraries
/usr/share/phpmyadmin/license.php
/usr/share/phpmyadmin/main.php
/usr/share/phpmyadmin/navigation.php
/usr/share/phpmyadmin/pdf_pages.php
/usr/share/phpmyadmin/pdf_schema.php
/usr/share/phpmyadmin/phpinfo.php
/usr/share/phpmyadmin/phpmyadmin.css.php
/usr/share/phpmyadmin/pmd
/usr/share/phpmyadmin/pmd_common.php
/usr/share/phpmyadmin/pmd_display_field.php
/usr/share/phpmyadmin/pmd_general.php
/usr/share/phpmyadmin/pmd_help.php
/usr/share/phpmyadmin/pmd_pdf.php
/usr/share/phpmyadmin/pmd_relation_new.php
/usr/share/phpmyadmin/pmd_relation_upd.php
/usr/share/phpmyadmin/pmd_save_pos.php
/usr/share/phpmyadmin/print.css
/usr/share/phpmyadmin/querywindow.php
/usr/share/phpmyadmin/server_binlog.php
/usr/share/phpmyadmin/server_collations.php
/usr/share/phpmyadmin/server_databases.php
/usr/share/phpmyadmin/server_engines.php
/usr/share/phpmyadmin/server_export.php
/usr/share/phpmyadmin/server_import.php
/usr/share/phpmyadmin/server_privileges.php
/usr/share/phpmyadmin/server_processlist.php
/usr/share/phpmyadmin/server_sql.php
/usr/share/phpmyadmin/server_status.php
/usr/share/phpmyadmin/server_variables.php
/usr/share/phpmyadmin/setup
/usr/share/phpmyadmin/show_config_errors.php
/usr/share/phpmyadmin/sql.php
/usr/share/phpmyadmin/tbl_addfield.php
/usr/share/phpmyadmin/tbl_alter.php
/usr/share/phpmyadmin/tbl_change.php
/usr/share/phpmyadmin/tbl_create.php
/usr/share/phpmyadmin/tbl_export.php
/usr/share/phpmyadmin/tbl_import.php
/usr/share/phpmyadmin/tbl_indexes.php
/usr/share/phpmyadmin/tbl_move_copy.php
/usr/share/phpmyadmin/tbl_operations.php
/usr/share/phpmyadmin/tbl_printview.php
/usr/share/phpmyadmin/tbl_relation.php
/usr/share/phpmyadmin/tbl_replace.php
/usr/share/phpmyadmin/tbl_row_action.php
/usr/share/phpmyadmin/tbl_select.php
/usr/share/phpmyadmin/tbl_sql.php
/usr/share/phpmyadmin/tbl_structure.php
/usr/share/phpmyadmin/themes
/usr/share/phpmyadmin/themes.php
/usr/share/phpmyadmin/transformation_overview.php
/usr/share/phpmyadmin/transformation_wrapper.php
/usr/share/phpmyadmin/translators.html
/usr/share/phpmyadmin/user_password.php
/usr/share/phpmyadmin/view_create.php
/usr/share/phpmyadmin/webapp.php
/usr/share/phpmyadmin/js/common.js
/usr/share/phpmyadmin/js/dom-drag.js
/usr/share/phpmyadmin/js/functions.js
/usr/share/phpmyadmin/js/indexes.js
/usr/share/phpmyadmin/js/keyhandler.js
/usr/share/phpmyadmin/js/mooRainbow
/usr/share/phpmyadmin/js/mootools-domready-rainbow.js
/usr/share/phpmyadmin/js/mootools.js
/usr/share/phpmyadmin/js/navigation.js
/usr/share/phpmyadmin/js/querywindow.js
/usr/share/phpmyadmin/js/server_privileges.js
/usr/share/phpmyadmin/js/tbl_change.js
/usr/share/phpmyadmin/js/tooltip.js
/usr/share/phpmyadmin/js/mooRainbow/images
/usr/share/phpmyadmin/js/mooRainbow/mooRainbow.css
/usr/share/phpmyadmin/js/mooRainbow/mooRainbow.js
/usr/share/phpmyadmin/js/mooRainbow/images/blank.gif
/usr/share/phpmyadmin/js/mooRainbow/images/moor_arrows.gif
/usr/share/phpmyadmin/js/mooRainbow/images/moor_boverlay.png
/usr/share/phpmyadmin/js/mooRainbow/images/moor_cursor.gif
/usr/share/phpmyadmin/js/mooRainbow/images/moor_slider.png
/usr/share/phpmyadmin/js/mooRainbow/images/moor_woverlay.png
/usr/share/phpmyadmin/js/mooRainbow/images/rainbow.png
/usr/share/phpmyadmin/lang/add_message.sh
/usr/share/phpmyadmin/lang/add_message_file.sh
/usr/share/phpmyadmin/lang/afrikaans-utf-8.inc.php
/usr/share/phpmyadmin/lang/albanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/arabic-utf-8.inc.php
/usr/share/phpmyadmin/lang/azerbaijani-utf-8.inc.php
/usr/share/phpmyadmin/lang/bangla-utf-8.inc.php
/usr/share/phpmyadmin/lang/basque-utf-8.inc.php
/usr/share/phpmyadmin/lang/belarusian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/belarusian_latin-utf-8.inc.php
/usr/share/phpmyadmin/lang/bosnian-utf-8.inc.php
/usr/share/phpmyadmin/lang/brazilian_portuguese-utf-8.inc.php
/usr/share/phpmyadmin/lang/bulgarian-utf-8.inc.php
/usr/share/phpmyadmin/lang/catalan-utf-8.inc.php
/usr/share/phpmyadmin/lang/check_lang.sh
/usr/share/phpmyadmin/lang/chinese_simplified-utf-8.inc.php
/usr/share/phpmyadmin/lang/chinese_traditional-utf-8.inc.php
/usr/share/phpmyadmin/lang/croatian-utf-8.inc.php
/usr/share/phpmyadmin/lang/czech-utf-8.inc.php
/usr/share/phpmyadmin/lang/danish-utf-8.inc.php
/usr/share/phpmyadmin/lang/dutch-utf-8.inc.php
/usr/share/phpmyadmin/lang/english-utf-8.inc.php
/usr/share/phpmyadmin/lang/estonian-utf-8.inc.php
/usr/share/phpmyadmin/lang/finnish-utf-8.inc.php
/usr/share/phpmyadmin/lang/french-utf-8.inc.php
/usr/share/phpmyadmin/lang/galician-utf-8.inc.php
/usr/share/phpmyadmin/lang/georgian-utf-8.inc.php
/usr/share/phpmyadmin/lang/german-utf-8.inc.php
/usr/share/phpmyadmin/lang/greek-utf-8.inc.php
/usr/share/phpmyadmin/lang/hebrew-utf-8.inc.php
/usr/share/phpmyadmin/lang/hindi-utf-8.inc.php
/usr/share/phpmyadmin/lang/hungarian-utf-8.inc.php
/usr/share/phpmyadmin/lang/indonesian-utf-8.inc.php
/usr/share/phpmyadmin/lang/italian-utf-8.inc.php
/usr/share/phpmyadmin/lang/japanese-utf-8.inc.php
/usr/share/phpmyadmin/lang/korean-utf-8.inc.php
/usr/share/phpmyadmin/lang/latvian-utf-8.inc.php
/usr/share/phpmyadmin/lang/lithuanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/macedonian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/malay-utf-8.inc.php
/usr/share/phpmyadmin/lang/mongolian-utf-8.inc.php
/usr/share/phpmyadmin/lang/norwegian-utf-8.inc.php
/usr/share/phpmyadmin/lang/persian-utf-8.inc.php
/usr/share/phpmyadmin/lang/polish-utf-8.inc.php
/usr/share/phpmyadmin/lang/portuguese-utf-8.inc.php
/usr/share/phpmyadmin/lang/remove_message.sh
/usr/share/phpmyadmin/lang/romanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/russian-utf-8.inc.php
/usr/share/phpmyadmin/lang/serbian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/serbian_latin-utf-8.inc.php
/usr/share/phpmyadmin/lang/sinhala-utf-8.inc.php
/usr/share/phpmyadmin/lang/slovak-utf-8.inc.php
/usr/share/phpmyadmin/lang/slovenian-utf-8.inc.php
/usr/share/phpmyadmin/lang/sort_lang.sh
/usr/share/phpmyadmin/lang/spanish-utf-8.inc.php
/usr/share/phpmyadmin/lang/swedish-utf-8.inc.php
/usr/share/phpmyadmin/lang/tatarish-utf-8.inc.php
/usr/share/phpmyadmin/lang/thai-utf-8.inc.php
/usr/share/phpmyadmin/lang/translatecount.sh
/usr/share/phpmyadmin/lang/turkish-utf-8.inc.php
/usr/share/phpmyadmin/lang/ukrainian-utf-8.inc.php
/usr/share/phpmyadmin/lang/uzbek_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/uzbek_latin-utf-8.inc.php
/usr/share/phpmyadmin/libraries/.htaccess
/usr/share/phpmyadmin/libraries/Config.class.php
/usr/share/phpmyadmin/libraries/Error.class.php
/usr/share/phpmyadmin/libraries/Error_Handler.class.php
/usr/share/phpmyadmin/libraries/File.class.php
/usr/share/phpmyadmin/libraries/Index.class.php
/usr/share/phpmyadmin/libraries/List.class.php
/usr/share/phpmyadmin/libraries/List_Database.class.php
/usr/share/phpmyadmin/libraries/Message.class.php
/usr/share/phpmyadmin/libraries/PMA.php
/usr/share/phpmyadmin/libraries/Partition.class.php
/usr/share/phpmyadmin/libraries/StorageEngine.class.php
/usr/share/phpmyadmin/libraries/Table.class.php
/usr/share/phpmyadmin/libraries/Theme.class.php
/usr/share/phpmyadmin/libraries/Theme_Manager.class.php
/usr/share/phpmyadmin/libraries/auth
/usr/share/phpmyadmin/libraries/blobstreaming.lib.php
/usr/share/phpmyadmin/libraries/blowfish.php
/usr/share/phpmyadmin/libraries/bookmark.lib.php
/usr/share/phpmyadmin/libraries/charset_conversion.lib.php
/usr/share/phpmyadmin/libraries/check_user_privileges.lib.php
/usr/share/phpmyadmin/libraries/cleanup.lib.php
/usr/share/phpmyadmin/libraries/common.inc.php
/usr/share/phpmyadmin/libraries/common.lib.php
/usr/share/phpmyadmin/libraries/config.default.php
/usr/share/phpmyadmin/libraries/core.lib.php
/usr/share/phpmyadmin/libraries/database_interface.lib.php
/usr/share/phpmyadmin/libraries/db_common.inc.php
/usr/share/phpmyadmin/libraries/db_events.inc.php
/usr/share/phpmyadmin/libraries/db_info.inc.php
/usr/share/phpmyadmin/libraries/db_links.inc.php
/usr/share/phpmyadmin/libraries/db_routines.inc.php
/usr/share/phpmyadmin/libraries/db_table_exists.lib.php
/usr/share/phpmyadmin/libraries/dbg
/usr/share/phpmyadmin/libraries/dbi
/usr/share/phpmyadmin/libraries/display_change_password.lib.php
/usr/share/phpmyadmin/libraries/display_create_database.lib.php
/usr/share/phpmyadmin/libraries/display_create_table.lib.php
/usr/share/phpmyadmin/libraries/display_export.lib.php
/usr/share/phpmyadmin/libraries/display_import.lib.php
/usr/share/phpmyadmin/libraries/display_select_lang.lib.php
/usr/share/phpmyadmin/libraries/display_tbl.lib.php
/usr/share/phpmyadmin/libraries/display_tbl_links.lib.php
/usr/share/phpmyadmin/libraries/engines
/usr/share/phpmyadmin/libraries/export
/usr/share/phpmyadmin/libraries/file_listing.php
/usr/share/phpmyadmin/libraries/footer.inc.php
/usr/share/phpmyadmin/libraries/grab_globals.lib.php
/usr/share/phpmyadmin/libraries/header.inc.php
/usr/share/phpmyadmin/libraries/header_http.inc.php
/usr/share/phpmyadmin/libraries/header_meta_style.inc.php
/usr/share/phpmyadmin/libraries/header_printview.inc.php
/usr/share/phpmyadmin/libraries/header_scripts.inc.php
/usr/share/phpmyadmin/libraries/iconv_wrapper.lib.php
/usr/share/phpmyadmin/libraries/import
/usr/share/phpmyadmin/libraries/import.lib.php
/usr/share/phpmyadmin/libraries/information_schema_relations.lib.php
/usr/share/phpmyadmin/libraries/ip_allow_deny.lib.php
/usr/share/phpmyadmin/libraries/js_escape.lib.php
/usr/share/phpmyadmin/libraries/kanji-encoding.lib.php
/usr/share/phpmyadmin/libraries/logging.lib.php
/usr/share/phpmyadmin/libraries/mult_submits.inc.php
/usr/share/phpmyadmin/libraries/mysql_charsets.lib.php
/usr/share/phpmyadmin/libraries/navigation_header.inc.php
/usr/share/phpmyadmin/libraries/ob.lib.php
/usr/share/phpmyadmin/libraries/opendocument.lib.php
/usr/share/phpmyadmin/libraries/parse_analyze.lib.php
/usr/share/phpmyadmin/libraries/plugin_interface.lib.php
/usr/share/phpmyadmin/libraries/relation.lib.php
/usr/share/phpmyadmin/libraries/relation_cleanup.lib.php
/usr/share/phpmyadmin/libraries/sanitizing.lib.php
/usr/share/phpmyadmin/libraries/select_lang.lib.php
/usr/share/phpmyadmin/libraries/select_server.lib.php
/usr/share/phpmyadmin/libraries/server_common.inc.php
/usr/share/phpmyadmin/libraries/server_links.inc.php
/usr/share/phpmyadmin/libraries/session.inc.php
/usr/share/phpmyadmin/libraries/sql_query_form.lib.php
/usr/share/phpmyadmin/libraries/sqlparser.data.php
/usr/share/phpmyadmin/libraries/sqlparser.lib.php
/usr/share/phpmyadmin/libraries/sqlvalidator.class.php
/usr/share/phpmyadmin/libraries/sqlvalidator.lib.php
/usr/share/phpmyadmin/libraries/string.lib.php
/usr/share/phpmyadmin/libraries/string_mb.lib.php
/usr/share/phpmyadmin/libraries/string_native.lib.php
/usr/share/phpmyadmin/libraries/string_type_ctype.lib.php
/usr/share/phpmyadmin/libraries/string_type_native.lib.php
/usr/share/phpmyadmin/libraries/tbl_common.php
/usr/share/phpmyadmin/libraries/tbl_info.inc.php
/usr/share/phpmyadmin/libraries/tbl_links.inc.php
/usr/share/phpmyadmin/libraries/tbl_properties.inc.php
/usr/share/phpmyadmin/libraries/tbl_replace_fields.inc.php
/usr/share/phpmyadmin/libraries/tbl_triggers.lib.php
/usr/share/phpmyadmin/libraries/tcpdf
/usr/share/phpmyadmin/libraries/transformations
/usr/share/phpmyadmin/libraries/transformations.lib.php
/usr/share/phpmyadmin/libraries/url_generating.lib.php
/usr/share/phpmyadmin/libraries/vendor_config.php
/usr/share/phpmyadmin/libraries/zip.lib.php
/usr/share/phpmyadmin/libraries/zip_extension.lib.php
/usr/share/phpmyadmin/libraries/auth/config.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/http.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/signon.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/swekey
/usr/share/phpmyadmin/libraries/auth/swekey/authentication.inc.php
/usr/share/phpmyadmin/libraries/auth/swekey/musbe-ca.crt
/usr/share/phpmyadmin/libraries/auth/swekey/swekey.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/swekey/swekey.php
/usr/share/phpmyadmin/libraries/dbg/setup.php
/usr/share/phpmyadmin/libraries/dbi/mysql.dbi.lib.php
/usr/share/phpmyadmin/libraries/dbi/mysqli.dbi.lib.php
/usr/share/phpmyadmin/libraries/engines/bdb.lib.php
/usr/share/phpmyadmin/libraries/engines/berkeleydb.lib.php
/usr/share/phpmyadmin/libraries/engines/binlog.lib.php
/usr/share/phpmyadmin/libraries/engines/innobase.lib.php
/usr/share/phpmyadmin/libraries/engines/innodb.lib.php
/usr/share/phpmyadmin/libraries/engines/memory.lib.php
/usr/share/phpmyadmin/libraries/engines/merge.lib.php
/usr/share/phpmyadmin/libraries/engines/mrg_myisam.lib.php
/usr/share/phpmyadmin/libraries/engines/myisam.lib.php
/usr/share/phpmyadmin/libraries/engines/ndbcluster.lib.php
/usr/share/phpmyadmin/libraries/engines/pbxt.lib.php
/usr/share/phpmyadmin/libraries/export/codegen.php
/usr/share/phpmyadmin/libraries/export/csv.php
/usr/share/phpmyadmin/libraries/export/excel.php
/usr/share/phpmyadmin/libraries/export/htmlexcel.php
/usr/share/phpmyadmin/libraries/export/htmlword.php
/usr/share/phpmyadmin/libraries/export/latex.php
/usr/share/phpmyadmin/libraries/export/ods.php
/usr/share/phpmyadmin/libraries/export/odt.php
/usr/share/phpmyadmin/libraries/export/pdf.php
/usr/share/phpmyadmin/libraries/export/sql.php
/usr/share/phpmyadmin/libraries/export/texytext.php
/usr/share/phpmyadmin/libraries/export/xls.php
/usr/share/phpmyadmin/libraries/export/xml.php
/usr/share/phpmyadmin/libraries/export/yaml.php
/usr/share/phpmyadmin/libraries/import/README
/usr/share/phpmyadmin/libraries/import/csv.php
/usr/share/phpmyadmin/libraries/import/docsql.php
/usr/share/phpmyadmin/libraries/import/ldi.php
/usr/share/phpmyadmin/libraries/import/sql.php
/usr/share/phpmyadmin/libraries/tcpdf/font
/usr/share/phpmyadmin/libraries/tcpdf/tcpdf.php
/usr/share/phpmyadmin/libraries/tcpdf/unicode_data.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans-bold.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans-bold.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusansb.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif-bold.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif-bold.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserifb.php
/usr/share/phpmyadmin/libraries/transformations/README
/usr/share/phpmyadmin/libraries/transformations/TEMPLATE
/usr/share/phpmyadmin/libraries/transformations/TEMPLATE_MIMETYPE
/usr/share/phpmyadmin/libraries/transformations/application_octetstream__download.inc.php
/usr/share/phpmyadmin/libraries/transformations/application_octetstream__hex.inc.php
/usr/share/phpmyadmin/libraries/transformations/generator.sh
/usr/share/phpmyadmin/libraries/transformations/global.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_jpeg__inline.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_jpeg__link.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_png__inline.inc.php
/usr/share/phpmyadmin/libraries/transformations/template_generator.sh
/usr/share/phpmyadmin/libraries/transformations/template_generator_mimetype.sh
/usr/share/phpmyadmin/libraries/transformations/text_plain__dateformat.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__external.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__formatted.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__imagelink.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__link.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__longToIpv4.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__sql.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__substr.inc.php
/usr/share/phpmyadmin/pmd/images
/usr/share/phpmyadmin/pmd/scripts
/usr/share/phpmyadmin/pmd/styles
/usr/share/phpmyadmin/pmd/images/2leftarrow.png
/usr/share/phpmyadmin/pmd/images/2leftarrow_m.png
/usr/share/phpmyadmin/pmd/images/2rightarrow.png
/usr/share/phpmyadmin/pmd/images/2rightarrow_m.png
/usr/share/phpmyadmin/pmd/images/ang_direct.png
/usr/share/phpmyadmin/pmd/images/bord.png
/usr/share/phpmyadmin/pmd/images/bottom.png
/usr/share/phpmyadmin/pmd/images/def.png
/usr/share/phpmyadmin/pmd/images/display_field.png
/usr/share/phpmyadmin/pmd/images/downarrow1.png
/usr/share/phpmyadmin/pmd/images/downarrow2.png
/usr/share/phpmyadmin/pmd/images/downarrow2_m.png
/usr/share/phpmyadmin/pmd/images/exec.png
/usr/share/phpmyadmin/pmd/images/exec_small.png
/usr/share/phpmyadmin/pmd/images/favicon.ico
/usr/share/phpmyadmin/pmd/images/grid.png
/usr/share/phpmyadmin/pmd/images/help.png
/usr/share/phpmyadmin/pmd/images/help_relation.png
/usr/share/phpmyadmin/pmd/images/pdf.png
/usr/share/phpmyadmin/pmd/images/relation.png
/usr/share/phpmyadmin/pmd/images/reload.png
/usr/share/phpmyadmin/pmd/images/resize.png
/usr/share/phpmyadmin/pmd/images/rightarrow1.png
/usr/share/phpmyadmin/pmd/images/rightarrow2.png
/usr/share/phpmyadmin/pmd/images/save.png
/usr/share/phpmyadmin/pmd/images/table.png
/usr/share/phpmyadmin/pmd/images/uparrow2_m.png
/usr/share/phpmyadmin/pmd/scripts/ajax.js
/usr/share/phpmyadmin/pmd/scripts/iecanvas.js
/usr/share/phpmyadmin/pmd/scripts/move.js
/usr/share/phpmyadmin/pmd/styles/default
/usr/share/phpmyadmin/pmd/styles/default/images
/usr/share/phpmyadmin/pmd/styles/default/style1.css
/usr/share/phpmyadmin/pmd/styles/default/images/1.png
/usr/share/phpmyadmin/pmd/styles/default/images/2.png
/usr/share/phpmyadmin/pmd/styles/default/images/3.png
/usr/share/phpmyadmin/pmd/styles/default/images/4.png
/usr/share/phpmyadmin/pmd/styles/default/images/5.png
/usr/share/phpmyadmin/pmd/styles/default/images/6.png
/usr/share/phpmyadmin/pmd/styles/default/images/7.png
/usr/share/phpmyadmin/pmd/styles/default/images/8.png
/usr/share/phpmyadmin/pmd/styles/default/images/FieldKey_small.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_char.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_date.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_int.png
/usr/share/phpmyadmin/pmd/styles/default/images/Header.png
/usr/share/phpmyadmin/pmd/styles/default/images/Header_Linked.png
/usr/share/phpmyadmin/pmd/styles/default/images/left_panel_butt.png
/usr/share/phpmyadmin/pmd/styles/default/images/left_panel_tab.png
/usr/share/phpmyadmin/pmd/styles/default/images/small_tab.png
/usr/share/phpmyadmin/pmd/styles/default/images/top_panel.png
/usr/share/phpmyadmin/setup/config.php
/usr/share/phpmyadmin/setup/frames
/usr/share/phpmyadmin/setup/index.php
/usr/share/phpmyadmin/setup/lib
/usr/share/phpmyadmin/setup/scripts.js
/usr/share/phpmyadmin/setup/styles.css
/usr/share/phpmyadmin/setup/validate.php
/usr/share/phpmyadmin/setup/frames/config.inc.php
/usr/share/phpmyadmin/setup/frames/form.inc.php
/usr/share/phpmyadmin/setup/frames/index.inc.php
/usr/share/phpmyadmin/setup/frames/menu.inc.php
/usr/share/phpmyadmin/setup/frames/servers.inc.php
/usr/share/phpmyadmin/setup/lib/.htaccess
/usr/share/phpmyadmin/setup/lib/ConfigFile.class.php
/usr/share/phpmyadmin/setup/lib/Form.class.php
/usr/share/phpmyadmin/setup/lib/FormDisplay.class.php
/usr/share/phpmyadmin/setup/lib/FormDisplay.tpl.php
/usr/share/phpmyadmin/setup/lib/common.inc.php
/usr/share/phpmyadmin/setup/lib/config_info.inc.php
/usr/share/phpmyadmin/setup/lib/form_processing.lib.php
/usr/share/phpmyadmin/setup/lib/forms.inc.php
/usr/share/phpmyadmin/setup/lib/index.lib.php
/usr/share/phpmyadmin/setup/lib/validate.lib.php
/usr/share/phpmyadmin/themes/darkblue_orange
/usr/share/phpmyadmin/themes/original
/usr/share/phpmyadmin/themes/darkblue_orange/css
/usr/share/phpmyadmin/themes/darkblue_orange/img
/usr/share/phpmyadmin/themes/darkblue_orange/info.inc.php
/usr/share/phpmyadmin/themes/darkblue_orange/layout.inc.php
/usr/share/phpmyadmin/themes/darkblue_orange/screen.png
/usr/share/phpmyadmin/themes/darkblue_orange/css/theme_right.css.php
/usr/share/phpmyadmin/themes/darkblue_orange/img/arrow_ltr.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/arrow_rtl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/asc_order.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_bookmark.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_browse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_calendar.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_comment.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_dbstatistics.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_deltbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_docs.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_docsql.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_drop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_edit.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_empty.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_engine.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_export.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_firstpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_ftext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_help.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_home.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_import.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_index.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_info.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_insrow.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_lastpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_minus.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_newdb.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_newtbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_nextpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_pdfdoc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_plus.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_prevpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_primary.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_print.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_props.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_relations.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_save.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sbrowse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sdb.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_search.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_selboard.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_select.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sql.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sqldoc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sqlhelp.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblanalyse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblexport.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblimport.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblops.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tbloptimize.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tipp.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_unique.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usradd.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrcheck.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrdrop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usredit.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrlist.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_view.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_views.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_browse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_deltbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_drop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_empty.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_firstpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_ftext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_index.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_insrow.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_lastpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_nextpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_prevpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_primary.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_sbrowse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_select.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_unique.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/error.ico
/usr/share/phpmyadmin/themes/darkblue_orange/img/item.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/item_ltr.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/item_rtl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/logo_left.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/logo_right.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/php_sym.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/pma_logo2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_asc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_asci.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_attention.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_cancel.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_cancel2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_db.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_desc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_error.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_error2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_fulltext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_host.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_info.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_lang.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_loggoff.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_notice.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_okay.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_partialtext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_passwd.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_process.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_really.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_reload.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_rights.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_status.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_success.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_tbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_theme.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_vars.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_views.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_warn.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/spacer.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/tbl_header.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/tbl_th.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/window-new.png
/usr/share/phpmyadmin/themes/original/css
/usr/share/phpmyadmin/themes/original/img
/usr/share/phpmyadmin/themes/original/info.inc.php
/usr/share/phpmyadmin/themes/original/layout.inc.php
/usr/share/phpmyadmin/themes/original/screen.png
/usr/share/phpmyadmin/themes/original/css/theme_left.css.php
/usr/share/phpmyadmin/themes/original/css/theme_print.css.php
/usr/share/phpmyadmin/themes/original/css/theme_right.css.php
/usr/share/phpmyadmin/themes/original/img/arrow_ltr.png
/usr/share/phpmyadmin/themes/original/img/arrow_rtl.png
/usr/share/phpmyadmin/themes/original/img/asc_order.png
/usr/share/phpmyadmin/themes/original/img/b_bookmark.png
/usr/share/phpmyadmin/themes/original/img/b_browse.png
/usr/share/phpmyadmin/themes/original/img/b_calendar.png
/usr/share/phpmyadmin/themes/original/img/b_comment.png
/usr/share/phpmyadmin/themes/original/img/b_dbstatistics.png
/usr/share/phpmyadmin/themes/original/img/b_deltbl.png
/usr/share/phpmyadmin/themes/original/img/b_docs.png
/usr/share/phpmyadmin/themes/original/img/b_docsql.png
/usr/share/phpmyadmin/themes/original/img/b_drop.png
/usr/share/phpmyadmin/themes/original/img/b_edit.png
/usr/share/phpmyadmin/themes/original/img/b_empty.png
/usr/share/phpmyadmin/themes/original/img/b_engine.png
/usr/share/phpmyadmin/themes/original/img/b_export.png
/usr/share/phpmyadmin/themes/original/img/b_firstpage.png
/usr/share/phpmyadmin/themes/original/img/b_ftext.png
/usr/share/phpmyadmin/themes/original/img/b_help.png
/usr/share/phpmyadmin/themes/original/img/b_home.png
/usr/share/phpmyadmin/themes/original/img/b_import.png
/usr/share/phpmyadmin/themes/original/img/b_index.png
/usr/share/phpmyadmin/themes/original/img/b_info.png
/usr/share/phpmyadmin/themes/original/img/b_insrow.png
/usr/share/phpmyadmin/themes/original/img/b_lastpage.png
/usr/share/phpmyadmin/themes/original/img/b_minus.png
/usr/share/phpmyadmin/themes/original/img/b_newdb.png
/usr/share/phpmyadmin/themes/original/img/b_newtbl.png
/usr/share/phpmyadmin/themes/original/img/b_nextpage.png
/usr/share/phpmyadmin/themes/original/img/b_pdfdoc.png
/usr/share/phpmyadmin/themes/original/img/b_plus.png
/usr/share/phpmyadmin/themes/original/img/b_prevpage.png
/usr/share/phpmyadmin/themes/original/img/b_primary.png
/usr/share/phpmyadmin/themes/original/img/b_print.png
/usr/share/phpmyadmin/themes/original/img/b_props.png
/usr/share/phpmyadmin/themes/original/img/b_relations.png
/usr/share/phpmyadmin/themes/original/img/b_save.png
/usr/share/phpmyadmin/themes/original/img/b_sbrowse.png
/usr/share/phpmyadmin/themes/original/img/b_sdb.png
/usr/share/phpmyadmin/themes/original/img/b_search.png
/usr/share/phpmyadmin/themes/original/img/b_selboard.png
/usr/share/phpmyadmin/themes/original/img/b_select.png
/usr/share/phpmyadmin/themes/original/img/b_sql.png
/usr/share/phpmyadmin/themes/original/img/b_sqldoc.png
/usr/share/phpmyadmin/themes/original/img/b_sqlhelp.png
/usr/share/phpmyadmin/themes/original/img/b_tblanalyse.png
/usr/share/phpmyadmin/themes/original/img/b_tblexport.png
/usr/share/phpmyadmin/themes/original/img/b_tblimport.png
/usr/share/phpmyadmin/themes/original/img/b_tblops.png
/usr/share/phpmyadmin/themes/original/img/b_tbloptimize.png
/usr/share/phpmyadmin/themes/original/img/b_tipp.png
/usr/share/phpmyadmin/themes/original/img/b_unique.png
/usr/share/phpmyadmin/themes/original/img/b_usradd.png
/usr/share/phpmyadmin/themes/original/img/b_usrcheck.png
/usr/share/phpmyadmin/themes/original/img/b_usrdrop.png
/usr/share/phpmyadmin/themes/original/img/b_usredit.png
/usr/share/phpmyadmin/themes/original/img/b_usrlist.png
/usr/share/phpmyadmin/themes/original/img/b_view.png
/usr/share/phpmyadmin/themes/original/img/b_views.png
/usr/share/phpmyadmin/themes/original/img/bd_browse.png
/usr/share/phpmyadmin/themes/original/img/bd_deltbl.png
/usr/share/phpmyadmin/themes/original/img/bd_drop.png
/usr/share/phpmyadmin/themes/original/img/bd_empty.png
/usr/share/phpmyadmin/themes/original/img/bd_firstpage.png
/usr/share/phpmyadmin/themes/original/img/bd_ftext.png
/usr/share/phpmyadmin/themes/original/img/bd_index.png
/usr/share/phpmyadmin/themes/original/img/bd_insrow.png
/usr/share/phpmyadmin/themes/original/img/bd_lastpage.png
/usr/share/phpmyadmin/themes/original/img/bd_nextpage.png
/usr/share/phpmyadmin/themes/original/img/bd_prevpage.png
/usr/share/phpmyadmin/themes/original/img/bd_primary.png
/usr/share/phpmyadmin/themes/original/img/bd_sbrowse.png
/usr/share/phpmyadmin/themes/original/img/bd_select.png
/usr/share/phpmyadmin/themes/original/img/bd_unique.png
/usr/share/phpmyadmin/themes/original/img/docs_menu_bg.png
/usr/share/phpmyadmin/themes/original/img/error.ico
/usr/share/phpmyadmin/themes/original/img/item.png
/usr/share/phpmyadmin/themes/original/img/item_ltr.png
/usr/share/phpmyadmin/themes/original/img/item_rtl.png
/usr/share/phpmyadmin/themes/original/img/logo_left.png
/usr/share/phpmyadmin/themes/original/img/logo_right.png
/usr/share/phpmyadmin/themes/original/img/php_sym.png
/usr/share/phpmyadmin/themes/original/img/pma_logo2.png
/usr/share/phpmyadmin/themes/original/img/s_asc.png
/usr/share/phpmyadmin/themes/original/img/s_asci.png
/usr/share/phpmyadmin/themes/original/img/s_attention.png
/usr/share/phpmyadmin/themes/original/img/s_cancel.png
/usr/share/phpmyadmin/themes/original/img/s_cancel2.png
/usr/share/phpmyadmin/themes/original/img/s_db.png
/usr/share/phpmyadmin/themes/original/img/s_desc.png
/usr/share/phpmyadmin/themes/original/img/s_error.png
/usr/share/phpmyadmin/themes/original/img/s_error2.png
/usr/share/phpmyadmin/themes/original/img/s_fulltext.png
/usr/share/phpmyadmin/themes/original/img/s_host.png
/usr/share/phpmyadmin/themes/original/img/s_info.png
/usr/share/phpmyadmin/themes/original/img/s_lang.png
/usr/share/phpmyadmin/themes/original/img/s_loggoff.png
/usr/share/phpmyadmin/themes/original/img/s_notice.png
/usr/share/phpmyadmin/themes/original/img/s_okay.png
/usr/share/phpmyadmin/themes/original/img/s_partialtext.png
/usr/share/phpmyadmin/themes/original/img/s_passwd.png
/usr/share/phpmyadmin/themes/original/img/s_process.png
/usr/share/phpmyadmin/themes/original/img/s_really.png
/usr/share/phpmyadmin/themes/original/img/s_reload.png
/usr/share/phpmyadmin/themes/original/img/s_rights.png
/usr/share/phpmyadmin/themes/original/img/s_status.png
/usr/share/phpmyadmin/themes/original/img/s_success.png
/usr/share/phpmyadmin/themes/original/img/s_tbl.png
/usr/share/phpmyadmin/themes/original/img/s_theme.png
/usr/share/phpmyadmin/themes/original/img/s_vars.png
/usr/share/phpmyadmin/themes/original/img/s_views.png
/usr/share/phpmyadmin/themes/original/img/s_warn.png
/usr/share/phpmyadmin/themes/original/img/spacer.png
/usr/share/phpmyadmin/themes/original/img/vertical_line.png
/usr/share/phpmyadmin/themes/original/img/window-new.png
/var/cache/apt/archives/phpmyadmin_4%3a3.2.1-1_all.deb
/var/lib/phpmyadmin
/var/lib/dpkg/info/phpmyadmin.conffiles
/var/lib/dpkg/info/phpmyadmin.config
/var/lib/dpkg/info/phpmyadmin.list
/var/lib/dpkg/info/phpmyadmin.md5sums
/var/lib/dpkg/info/phpmyadmin.postinst
/var/lib/dpkg/info/phpmyadmin.postrm
/var/lib/dpkg/info/phpmyadmin.prerm
/var/lib/dpkg/info/phpmyadmin.templates
/var/lib/mysql/phpmyadmin
/var/lib/phpmyadmin/blowfish_secret.inc.php
/var/lib/phpmyadmin/config.inc.php
/var/lib/ucf/cache/:etc:dbconfig-common:phpmyadmin.conf
/var/lib/ucf/cache/:etc:phpmyadmin:config-db.php
```


Can you verify that you have the libapache2-mod-php5 installed?

---

### Post by stef25 on 2009-10-30
Sure, how can I verify?

---

### Post by Giblet5 on 2009-10-30
```
sudo dpkg -l | grep apache
```

---

### Post by stef25 on 2009-10-30
ii  apache2                                    2.2.12-1ubuntu2                            Apache HTTP Server metapackage
ii  apache2-mpm-prefork                        2.2.12-1ubuntu2                            Apache HTTP Server - traditional non-threade
ii  apache2-utils                              2.2.12-1ubuntu2                            utility programs for webservers
ii  apache2.2-bin                              2.2.12-1ubuntu2                            Apache HTTP Server common binary files
ii  apache2.2-common                           2.2.12-1ubuntu2                            Apache HTTP Server common files
ii  libapache2-mod-php5                        5.2.10.dfsg.1-2ubuntu6                     server-side, HTML-embedded scripting languag

---

### Post by Giblet5 on 2009-10-30
Then I've got nuthin'. It worked out of the box for me.

Sorry I wasted your time. :(

---

### Post by stef25 on 2009-10-30
Balls ... Any DB GUI alternatives available?

Thanks for your time, I do appreciate it.

---

### Post by Giblet5 on 2009-10-30
> **stef25 said:**
> Balls ... Any DB GUI alternatives available?

Thanks for your time, I do appreciate it.

Sure. ```
sudo apt-get install mysql-admin
```

It'll show up in Applications -> Programming -> MySQL Administrator.

---

### Post by Statik on 2009-10-30
Last time I installed phpMyAdmin, the following line had to be added to the bottom of /etc/apache2/apache2.conf
```
Include /etc/phpmyadmin/apache.conf
```

and then apache restarted:
```
sudo /etc/init.d/apache2 restart
```

Statik

---

### Post by stef25 on 2009-10-31
I only have a file called apache2.conf.gz located in /usr/share/doc/apache2/examples/apache2

that's not normal is it?

---

### Post by HNS-I on 2009-10-31
You say the file apache.conf has some redirect Directives.
I think your httpd.conf is missing the allowoverride directive maybe?
I think including /etc/phpmyadmin/apache.conf wouldn't help since your friend moved it to the document directory.

---

### Post by stef25 on 2009-10-31
I know what the httpd.conf file is but when I search for it, nothing show up. Where should this file be located?

---

### Post by HNS-I on 2009-10-31
> **stef25 said:**
> I know what the httpd.conf file is but when I search for it, nothing show up. Where should this file be located?

Mine is in /etc/apache2/

---

### Post by Caysho on 2009-11-01
> **Statik said:**
> Last time I installed phpMyAdmin, the following line had to be added to the bottom of /etc/apache2/apache2.conf
```
Include /etc/phpmyadmin/apache.conf
```

and then apache restarted:
```
sudo /etc/init.d/apache2 restart
```

Statik

Thanks, phpmyadmin works now.  This was not required using an earlier karmic build, so a new bug has appeared in the final release.

---

