---
title: "Ubuntu 10.10 Cacti Plugin Architecture Install"
date: 2011-03-29
forum: General Help
---

### Post by cnrz on 2011-03-29
Hello,

We are instaling Cacti 0.8.7g on Ubuntu Server 10.10.  Following the link [http://www.ubuntugeek.com/install-and-configure-cacti-monitoring-tool-in-ubuntu-810-intrepid-ibex-server.html](http://www.ubuntugeek.com/install-and-configure-cacti-monitoring-tool-in-ubuntu-810-intrepid-ibex-server.html) 

All goes ok, and we may see the graphs forming.  But when it comes to PIA (Plugin Architecture) installation, we are not successful. 

We have followed the 2 ways of installing the PIA cacti-plugin-0.8.7g-PA-v2.8.tar, following the link [http://docs.cacti.net/manual:087:1_installation.9_pia](http://docs.cacti.net/manual:087:1_installation.9_pia).  Both the using pre-patched files method, and using the patch.

After installation we tried to edit the config.php and global.php under /usr/share/cacti/site/include according to this links:

[http://ubuntuforums.org/showthread.php?t=1428193](http://ubuntuforums.org/showthread.php?t=1428193)
[http://cactiusers.org/forums/topic1631.html](http://cactiusers.org/forums/topic1631.html) 


What we end up is that if try to login to Cacti with [http://IP_Address/cacti](http://IP_Address/cacti), a white empty page opens. If we look at the /var/log/apache2/error.log we see that 

PHP Parse error:  syntax error, unexpected '[' in /usr/share/cacti/site/include/global.php on line 105.

Line 105 of the global.php is 105 $config["library_path"] = ereg_replace("(.*[\\\/])include", "\\1lib", dirname(__FILE__));

Why may we getting this error, and how can we correct it? 

Thanks in Advance,
Best Regards,






      1 <?php
      2 /*
      3  +-------------------------------------------------------------------------+
      4  | Copyright (C) 2004-2010 The Cacti Group                                 |
      5  |                                                                         |
      6  | This program is free software; you can redistribute it and/or           |
      7  | modify it under the terms of the GNU General Public License             |
      8  | as published by the Free Software Foundation; either version 2          |
      9  | of the License, or (at your option) any later version.                  |
     10  |                                                                         |
     11  | This program is distributed in the hope that it will be useful,         |
     12  | but WITHOUT ANY WARRANTY; without even the implied warranty of          |
     13  | MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the           |
     14  | GNU General Public License for more details.                            |
     15  +-------------------------------------------------------------------------+
     16  | Cacti: The Complete RRDTool-based Graphing Solution                     |
     17  +-------------------------------------------------------------------------+
     18  | This code is designed, written, and maintained by the Cacti Group. See  |
     19  | about.php and/or the AUTHORS file for specific developer information.   |
     20  +-------------------------------------------------------------------------+
     21  | [http://www.cacti.net/](http://www.cacti.net/)                                                   |
     22  +-------------------------------------------------------------------------+
     23 */
     24 
     25 /*
     26    !!! IMPORTANT !!!
     27 
     28    The following defaults are not to be altered.  Please refer to
     29    include/config.php for user configurable database settings.
     30 
     31 */
     32 
     33 /* Default database settings*/
     34 $database_type = "mysql";
     35 $database_default = "cacti";
     36 $database_hostname = "localhost";
     37 $database_username = "cactiuser";
     38 $database_password = "cactiuser";
     39 $database_port = "3306";
     40 
     41 /* Default session name - Session name must contain alpha characters */
     42 $cacti_session_name = "Cacti";
     43 
     44 /* Include configuration */
     45 include(dirname(__FILE__) . "/config.php");
     46 
     47 if (isset($config["cacti_version"])) {
     48         die("Invalid include/config.php file detected.");
     49         exit;
     50 }
     51 
     52 /* display ALL errors,
     53  * but suppress deprecated warnings as a workaround until 088 */
     54 if (defined("E_DEPRECATED")) {
     55         error_reporting(E_ALL ^ E_DEPRECATED);
     56 }else{
     57         error_reporting(E_ALL);
     58 }
     59 
     60 /* Files that do not need http header information - Command line scripts */
     61 $no_http_header_files = array(
     62         "cmd.php",
     63         "poller.php",
     64         "poller_commands.php",
     65         "script_server.php",
     66         "query_host_cpu.php",
     67         "query_host_partitions.php",
     68         "sql.php",
     69         "ss_host_cpu.php",
     70         "ss_host_disk.php",
     71         "ss_sql.php",
     72         "add_device.php",
     73         "add_graphs.php",
     74         "add_perms.php",
     75         "add_tree.php",
     76         "copy_user.php",
     77         "host_update_template.php",
     78         "poller_export.php",
     79         "poller_graphs_reapply_names.php",
     80         "poller_output_empty.php",
     81         "poller_reindex_hosts.php",
     82         "rebuild_poller_cache.php",
     83         "repair_database.php",
     84         "structure_rra_paths.php"
     85 );
     86 
     87 $config = array();
     88 $colors = array();
     89 
     90 /* this should be auto-detected, set it manually if needed */
     91 $config["cacti_server_os"] = (strstr(PHP_OS, "WIN")) ? "win32" : "unix";
     92 
     93 /* built-in snmp support */
     94 $config["php_snmp_support"] = function_exists("snmpget");
     95 
     96 /* set URL path */
     97 if (! isset($url_path)) {
     98         $url_path = "";
     99 }
    100 $config['url_path'] = $url_path;
    101 define('URL_PATH', $url_path);
    102 
    103 /* used for includes */
    104 $config["base_path"] = strtr(ereg_replace("(.*)[\\\/]include", "\\1", dirname(__FILE__)), "\\", "/");
    105 $config["library_path"] = ereg_replace("(.*[\\\/])include", "\\1lib", dirname(__FILE__));
    106 $config["include_path"] = dirname(__FILE__);
    107 $config["rra_path"] = "var/lib/cacti/rra";
    108 
    109 /* colors */
    110 $colors["dark_outline"] = "454E53";
    111 $colors["dark_bar"] = "AEB4B7";
    112 $colors["panel"] = "E5E5E5";
    113 $colors["panel_text"] = "000000";
    114 $colors["panel_link"] = "000000";
    115 $colors["light"] = "F5F5F5";
    116 $colors["alternate"] = "E7E9F2";
    117 $colors["panel_dark"] = "C5C5C5";
    118 
    119 $colors["header"] = "00438C";
    120 $colors["header_panel"] = "6d88ad";
    121 $colors["header_text"] = "ffffff";
    122 $colors["form_background_dark"] = "E1E1E1";
    123 
    124 $colors["form_alternate1"] = "F5F5F5";
    125 $colors["form_alternate2"] = "E5E5E5";
    126 
    127 if ((!in_array(basename($_SERVER["PHP_SELF"]), $no_http_header_files, true)) && ($_SERVER["PHP_SELF"] != "")) {
    128         /* Sanity Check on "Corrupt" PHP_SELF */
    129         if ($_SERVER["SCRIPT_NAME"] != $_SERVER["PHP_SELF"]) {
    130                 echo "\nInvalid PHP_SELF Path \n";
    131                 exit;
    132         }
    133 
    134         /* we don't want these pages cached */
    135         header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
    136         header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT");
    137         header("Cache-Control: no-store, no-cache, must-revalidate");
    138         header("Cache-Control: post-check=0, pre-check=0", false);
    139         header("Pragma: no-cache");
    140         /* prevent IE from silently rejects cookies sent from third party sites. */
    141         header('P3P: CP="CAO PSA OUR"');
    142 
    143         /* initilize php session */
    144         session_name($cacti_session_name);
    145         session_start();
    146 
    147         /* detect and handle get_magic_quotes */
    148         if (!get_magic_quotes_gpc()) {
    149                 function addslashes_deep($value) {
    150                         $value = is_array($value) ? array_map('addslashes_deep', $value) : addslashes($value);
    151                         return $value;
    152                 }
    153 
    154                 $_POST   = array_map('addslashes_deep', $_POST);
    155                 $_GET    = array_map('addslashes_deep', $_GET);
    156                 $_COOKIE = array_map('addslashes_deep', $_COOKIE);
    157         }
    158 
    159         /* make sure to start only only Cacti session at a time */
    160         if (!isset($_SESSION["cacti_cwd"])) {
    161                 $_SESSION["cacti_cwd"] = $config["base_path"];
    162         }else{
    163                 if ($_SESSION["cacti_cwd"] != $config["base_path"]) {
    164                         session_unset();
    165                         session_destroy();
    166                 }
    167         }
    168 }
    169 
    170 /* emulate 'register_globals' = 'off' if turned on */
    171 if ((bool)ini_get("register_globals")) {
    172         $not_unset = array("_GET", "_POST", "_COOKIE", "_SERVER", "_SESSION", "_ENV", "_FILES", "database_type", "database_default", "database_hostname", "database_username", "database_password", "config", "colors");
    173 
    174         /* Not only will array_merge give a warning if a parameter is not an array, it will
    175         * actually fail. So we check if HTTP_SESSION_VARS has been initialised. */
    176         if (!isset($_SESSION)) {
    177                 $_SESSION = array();
    178         }
    179 
    180         /* Merge all into one extremely huge array; unset this later */
    181         $input = array_merge($_GET, $_POST, $_COOKIE, $_SERVER, $_SESSION, $_ENV, $_FILES);
    182 
    183         unset($input["input"]);
    184         unset($input["not_unset"]);
    185 
    186         while (list($var,) = @each($input)) {
    187                 if (!in_array($var, $not_unset)) {
    188                         unset($$var);
    189                 }
    190         }
    191 
    192         unset($input);
    193 }
    194 
    195 /* include base modules */
    196 include($config["library_path"] . "/adodb/adodb.inc.php");
    197 include("/usr/share/php/adodb/adodb.inc.php");
    198 /* connect to the database server */
    199 db_connect_real($database_hostname, $database_username, $database_password, $database_default, $database_type, $database_port);
    200 
    201 /* include additional modules */
    202 include_once($config["library_path"] . "/functions.php");
    203 include_once($config["include_path"] . "/global_constants.php");
    204 include_once($config["library_path"] . "/plugins.php");
    205 include_once($config["include_path"] . "/plugins.php");
    206 include_once($config["include_path"] . "/global_arrays.php");
    207 include_once($config["include_path"] . "/global_settings.php");
    208 include_once($config["include_path"] . "/global_form.php");
    209 include_once($config["library_path"] . "/html.php");
    210 include_once($config["library_path"] . "/html_form.php");
    211 include_once($config["library_path"] . "/html_utility.php");
    212 include_once($config["library_path"] . "/html_validate.php");
    213 include_once($config["library_path"] . "/variables.php");
    214 include_once($config["library_path"] . "/auth.php");
    215 
    216 api_plugin_hook("config_insert");
    217 
    218 /* current cacti version */
    219 $config["cacti_version"] = "0.8.7g";
    220 
    221 ?>

---

### Post by cnrz on 2011-03-29
Hello,
What we have changed inorder to troubleshoot is as follows:

1. We commented out the line 105, inorder to observe this case, but even if commented out the error did not change.
2. Since the Error did not change, we removed the lines and given static  entries for base_path and library_path values as below. But even in this case the error did not change.

 #REMOVED LINES:
$config["base_path"] = strtr(ereg_replace(“(.*)[\/\\]include”, “\\1&#8243;, dirname(__FILE__)), “\\”, “/”);
$config["library_path"] = ereg_replace(“(.*[\/\\])include”, “\\1lib”, dirname(__FILE__));
  #ADDED LINES:
$config["base_path"] = ‘/usr/share/cacti/site’;
$config["library_path"] = ‘/usr/share/cacti/site/lib’;
  
3. We removed the commented out lines and given a space instead of line 105, i.e. line 105 is a blank line. Even in this case the error does not change, which is very interesting.
PHP Parse error:  syntax error, unexpected '[' in /usr/share/cacti/site/include/global.php on line 105

Is there any possibility that the file is affected from some other parameter or value?
 

Best Regards,

---

### Post by cnrz on 2011-03-30
Hi all, 

After going through some changes, for both files, the Cacti Plugin Architecture was installed and we may hereafter install plugins easily. The main point is changing some of the global.php, config.php and /etc/cacti/debian.php files. In the documentation debian.php file is not mentioned but it definitely affects the way PIA works. Only this link mentions briefly ([FONT=&quot][http://forums.cacti.net/viewtopic.php?f=20&t=36499&p=209839#p209839](http://forums.cacti.net/viewtopic.php?f=20&t=36499&p=209839#p209839)). [/FONT] There may be additional methods but since this is working we think it may be used for Ubuntu Server 10.10.


The Installation consists of:
1. copying the PIA from cactiusers.org by: wget [http://mirror.cactiusers.org/downloads/plugins/cacti-plugin-0.8.7g-PA-v2.8.tar.gz](http://mirror.cactiusers.org/downloads/plugins/cacti-plugin-0.8.7g-PA-v2.8.tar.gz) 

2. tar -zxvf cacti-plugin-0.8.7g-PA-v2.8.tar.gz 

3. sudo  cp cacti-plugin-arch/* /usr/share/cacti/site/ -R

4. Goto the folder cacti-plugin-arch (which you extracted from the download). In this folder is the pa.sql.Import the pa.sql file to the cacti database. If this is not done, graphics are not seen on the cacti web site:
/usr/local/mysql/bin/mysql --user=root --password=rootpw cacti < pa.sql  (or mysql cacti < pa.sql -u root -p rootpw). Here you should write the root password given during the installation instead of rootpw. 
The Changes made from the original installation files coming within cacti-plugin-0.8.7g-PA-v2.8.tar file is as follows: (Other lines left exactly the same, just copy them to /usr/share/cacti/site

STEP1: Change /usr/share/cacti/site/include/global.php as follows:

/* Line 37 $database_username = "cactiuser"; */

$database_username = "cacti";
/* Line 38 $database_password = "cactiuser"; */

$database_password = "enter your pass given during installation(not cactiuser)";

/Line 105 *$config['url_path'] = $url_path;*/

$config["url_path"] = '/cacti/';

/* Line 112 $config["rra_path"] = $config["base_path"] . '/rra';*/

$config["rra_path"] = "/var/lib/cacti/rra";

/* Line 202 include($config["library_path"] . "/adodb/adodb.inc.php");*/

include("/usr/share/php/adodb/adodb.inc.php");


STEP2: Change /usr/share/cacti/site/include/config.php as follows:
config.php is as follows (we don't do any changes in this file, all the additions are made to the debian.php file, but the patch file requires some changes to be made, we did the database setting 
configuration on the /etc/cacti/debian.php file. $url_path = "/"; parameter is also changed on the global.php file. 

<?php


/* make sure these values refect your actual database/host/user/password */
$database_type = "mysql";
require('/etc/cacti/debian.php');

/* Default session name - Session name must contain alpha characters */
#$cacti_session_name = "Cacti";

?>

/* load up old style plugins here */

$plugins = array();

STEP3: Change /etc/cacti/debian.php
/* Lines 14 and 15 */
$database_username='cacti';
$database_password='enter your pass given during the installation';
Add the following lines:
/* load up old style plugins here. You need to enter some old style plugins like syslog, but for new plugins you don't need to enter them here, by default they appear on plugin management link on the left  */
$plugins = array();
$plugins[] = ‘ntop’;


Also, as a second alternative method to the above procedure, just use the patch command, but before using  this command  make sure that apache2 and mysql services are stopped with /etc/init.d/apache2 stop, and /etc/init.d/mysql stop. 

1. Copy the cacti-plugin-arch.diff file to /usr/share/cacti/site with sudo cp cacti-plugin-arch.dif  /usr/share/cacti/site command

patch -p1 -N --dry-run < cacti-plugin-arch.diff (see this does not give any errors
patch -p1 -N < cacti-plugin-arch.diff

2. Import the pa.sql file to the cacti database. If this is not done,
graphics are not seen on the cacti web site. 
/usr/local/mysql/bin/mysql --user=root --password=rootpw cacti < pa.sql

3. After patching don't forget to restart both apache2 and mysql with
/etc/init.d/apache2 start
/etc/init.d/mysql start

---

### Post by Oblong_Cheese on 2012-03-01
Thank-you so much for this simple guide, I got it working first go!

---

