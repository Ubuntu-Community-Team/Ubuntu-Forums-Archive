---
title: "How do you install Pear PC"
date: 2011-01-12
forum: General Help
---

### Post by mindrifter on 2011-01-12
I don't know how to install pearpc. I'm running Ubuntu 8.04.

---

### Post by matt_symes on 2011-01-12
Hi

Is it in the repositories in your version ? It is in 10.04. Search for pearpc.

Hopefully this may help.

[http://ubuntuforums.org/showthread.php?t=389767&highlight=pearpc](http://ubuntuforums.org/showthread.php?t=389767&highlight=pearpc)

Kind regards

---

### Post by mindrifter on 2011-01-12
no, it's not in the respository

---

### Post by OldManRiver on 2012-03-01
All,

Here is a script for installing most of the Pear stuff.  You will have to run the commands:
```
pear list > /home/installed-pear-list.txt
pear remote-list /home/notinstalled-pear-list.txt

```
And look at these files after running the script, to see what other addons and extensions you want.
```
#! /bin/bash
# Script to Install HTML Quick Forms with Pear
# Must be in SUDO state to run
# Script designed for Ubuntu 10.04 and later versions

# Add Pear related repositories
add-apt-repository ppa:ubuntu-toolchain-r/test;
add-apt-repository ppa:andphe/php && apt-get update;

# Install Pear & Test
apt-get install php-pear;

# Check on installed and Possible Pear Add-ons/Extensions
# pear list > /home/installed-pear-list.txt;
# pear remote-list /home/notinstalled-pear-list.txt;

# Install Pear Addons
pear install CodeGen;
pear install CodeGen_MySQL;
pear install CodeGen_MySQL_Plugin;
pear install Contact_AddressBook;
pear install Date_Holidays_USA;
pear install DB;
pear install DB_ado;
pear install DB_DataObject;
pear install DB_QueryTool;
pear install DB_ldap;
pear install DB_ldap2;
pear install DB_DataObject_FormBuilder;
pear install DB_Table;
pear install DBA;
pear install DBA_Relational;
pear install File_Bittorrent;
pear install File_Cabinet;
pear install File_CSV_DataSource;
pear install File_Find;
pear install File_DNS;
pear install File_PDF;
pear install File_Sitemap;
pear install Genealogy_Gedcom;
pear install HTML_BBCodeParser;
pear install HTML_Common;
pear install HTML_CSS;
pear install HTML_Form;
pear install HTML_Menu;
pear install HTML_Page;
pear install HTML_Progress;
pear install HTML_Select;
pear install HTML_Table;
pear install HTML_Table_Matrix;
pear install HTML_TreeMenu;
pear install HTTP_Client;
pear install HTTP_Download;
pear install HTTP_Header;
pear install HTTP_Server;
pear install HTTP_Upload;
pear install MDB;
pear install MDB_QueryTool;
pear install MDB2;
pear install MDB2_Driver_sqlsrv;
pear install MDB2_Driver_pgsql;
pear install MDB2_Driver_mysql;
pear install MDB2_Schema-0.8.5;
pear install MDB2_TableBrowser;
pear install MDB2_Driver_odbc;
pear install Payment_Clieop;
pear install Payment_PayPal_SOAP;
pear install Payment_Process;
pear install PEAR_Frontend_Gtk;
pear install PEAR_Frontend_Web;
pear install PEAR_PackageFileManager;
pear install PEAR_PackageFileManager_GUI_Gtk;
pear install PEAR_Frontend_Gtk2;
pear install PEAR_PackageFileManager_Frontend;
pear install PEAR_PackageFileManager_Frontend_Web;
pear install pearweb;
pear install PHP_Debug;
pear install PHP_CodeSniffer;
pear install PHP_Parser;
pear install PHPDoc;
pear install PHPExcel;
pear install Services_PageRank;
pear install Services_JSON;
pear install Services_W3C_CSSValidator;
pear install SOAP;
pear install SOAP_Interop;
pear install Spreadsheet_Excel_Writer;
pear install SQL_Parser;
pear install XML_RPC;
pear install XML_RPC2;

# Install Quick Forms
pear install HTML_QuickForm;
pear install HTML_QuickForm_advmultiselect;
pear install HTML_QuickForm_altselect;
pear install HTML_QuickForm_CAPTCHA;
pear install HTML_QuickForm_Controller;
pear install HTML_QuickForm_DHTMLRulesTableless;
pear install HTML_QuickForm_ElementGrid;
pear install HTML_QuickForm_Livesearch;
pear install HTML_QuickForm_Renderer_Tableless;
pear install HTML_QuickForm_Rule_Spelling;
pear install HTML_QuickForm_SelectFilter;
pear install HTML_QuickForm2;

# Install PEAR GUIs
pear channel-discover pear.chiaraquartet.net;
# pear install chiara/Chiara_PEAR_Server;
pear install --alldeps channel://pear.chiaraquartet.net/Chiara_PEAR_Server-0.20.0;
pear upgrade PEAR;
# The next line configures the Pear GUIs
pear run-scripts chiara/Chiara_PEAR_Server
# Call the Pear GUIs with:
# http://hostname/admin.php
# where "hostname" is the name you defined in the setup/config script

```

This is not error free, but will do over 80% of what you need with PEAR!

**Note:**
If your site does not link correctly you may need to run the following script:
```
#! /bin/bash

echo Adding Apache Aliases;
echo "
    	Alias /pear/ "/usr/share/php/htdocs/"
    	<Directory "/usr/share/php/htdocs/">
        	Options Indexes MultiViews FollowSymLinks
        	AllowOverride All
        	Order allow,deny
        	allow from all
    	</Directory>" >> /etc/apache2/aliases.conf;
echo "
    	Alias /pear/ "/usr/share/php/htdocs/"
    	<Directory "/usr/share/php/htdocs/">
        	Options Indexes MultiViews FollowSymLinks
        	AllowOverride All
        	Order allow,deny
        	allow from all
    	</Directory>" >> /etc/apache2/sites-enabled/000-default;
/etc/init.d/apache2 restart;

```
Edit the two files and fix syntax if errors occur!

Hope you enjoy!

OMR

---

### Post by oldos2er on 2012-03-01
Closed, necromancy.

---

