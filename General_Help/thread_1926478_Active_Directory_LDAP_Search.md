---
title: "Active Directory LDAP Search"
date: 2012-02-16
forum: General Help
---

### Post by sobrien on 2012-02-16
I wanted to look up some information from various fields of our Active Directory LDAP server from PHP running on Ubuntu. I thought I would contribute the results of that research here. Along with PHP5 and Apache2, you need to apt-get install php5-ldap

<?php
/**************************************************
  Bind to an Active Directory LDAP server and look
  something up. 
***************************************************/
  $SearchFor="fred";               //What string do you want to find?
  $SearchField="samaccountname";   //In what Active Directory field do you want to search for the string?

  $LDAPHost = "10.10.10.10";       //Your LDAP server DNS Name or IP Address
  $dn = "DC=whatever,DC=whatever"; //Put your Base DN here
  $LDAPUserDomain = "@something.something";  //Needs the @, but not always the same as the LDAP server domain
  $LDAPUser = "ldapuserid";        //A valid Active Directory login
  $LDAPUserPassword = "passforuser";
  $LDAPFieldsToFind = array("cn", "givenname", "samaccountname", "homedirectory", "telephonenumber", "mail");
    
  $cnx = ldap_connect($LDAPHost) or die("Could not connect to LDAP");
  ldap_set_option($cnx, LDAP_OPT_PROTOCOL_VERSION, 3);  //Set the LDAP Protocol used by your AD service
  ldap_set_option($cnx, LDAP_OPT_REFERRALS, 0);         //This was necessary for my AD to do anything
  ldap_bind($cnx,$LDAPUser.$LDAPUserDomain,$LDAPUserPassword) or die("Could not bind to LDAP");
  error_reporting (E_ALL ^ E_NOTICE);   //Suppress some unnecessary messages
  $filter="($SearchField=$SearchFor*)"; //Wildcard is * Remove it if you want an exact match
  $sr=ldap_search($cnx, $dn, $filter, $LDAPFieldsToFind);
  $info = ldap_get_entries($cnx, $sr);
 
  for ($x=0; $x<$info["count"]; $x++) {
    $sam=$info[$x]['samaccountname'][0];
    $giv=$info[$x]['givenname'][0];
    $tel=$info[$x]['telephonenumber'][0];
    $email=$info[$x]['mail'][0];
    $nam=$info[$x]['cn'][0];
    $dir=$info[$x]['homedirectory'][0];
    $dir=strtolower($dir);
    $pos=strpos($dir,"home");
    $pos=$pos+5;
    if (stristr($sam, "$SearchFor") && (strlen($dir) > 8)) {
      print "\nActive Directory says that:\n";
      print "CN is: $nam \n";
      print "SAMAccountName is: $sam \n";
      print "Given Name is: $giv \n";
      print "Telephone is: $tel \n";
      print "Home Directory is: $dir \n";
    }   
  }   
  if ($x==0) { print "Oops, $SearchField $SearchFor was not found. Please try again.\n"; }
?>

---

