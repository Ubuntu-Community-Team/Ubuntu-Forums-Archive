---
title: "help !sbin/runscript: bad interpreter"
date: 2006-02-17
forum: General Help
---

### Post by konradsa on 2006-02-17
Hi, I have the following script I am trying to execute in Ubuntu 5.10. I already patched and installed a kernel that allows undervolting. Now I would like to automatically apply my new voltages at startup with the following script:

#!/sbin/runscript
# Copyright 1999-2005 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: $

depend() 
{
  need localmount
  need logger
}


do_error()
{
  # Display an error
  # $1: Error message

  eerror $1
  eerror "see [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU) for further information"
  eend 1
}

sysfs_check() 
{
  # Check that the sysfs interface exists

  if ! [ -e ${VTABLE_PATH} ]; then
    logger "SysFs voltage_table not found. Can't modify CPU voltage table. (${VTABLE_PATH})"
    eerror "SysFs voltage_table not found. Can't modify CPU voltage table. (${VTABLE_PATH})"
    eerror "It seems that the undervolting patch has not been applied to the kernel"
    do_error "or that the file /etc/conf.d/undervolt is not correctly configured."
    return 1
  fi
}

einfo_tables()
{
  # display current table and a custom table
  # $1 : custom table to display

  # Display the voltage table currently used by the CPU
  einfo "Current table:     "`cat ${VTABLE_PATH} `

  # Display the custom voltage table configured in /etc/conf.d//undervolt
  einfo "Configured table:  ${1}"
}

vtable_check()
{
  # Check that the table given in parameter has the same number of values that the current table.
  # $1 : custom table to check

  # Get number of values of current table
  sysfs_count=`cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table | tr "," " " | wc -w`
  # Get number of values of custom table
  table_count=`echo ${1} | tr "," " " | wc -w`
  # check if same number of values in both tables
  if ! [ ${sysfs_count} -eq ${table_count} ]; then
    logger "Current SysFs voltage_table has not the same number of values than the configured custom table"
    eerror "Current SysFs voltage_table has not the same number of values than the configured custom table"
    einfo_tables ${1}
    do_error "Check your configuration in /etc/conf.d/undervolt"
    return 1
  fi
}

set_custom_table()
{
  # Set a custom table through the sysfs interface
  # $1 : custom table to set

  # Display current table and custom table that will be set
  einfo_tables ${1}

  # Write the custom voltage to the SysFS interface and display the
  # new voltage table that is now used by the CPU if there is no error
  echo ${1} > ${VTABLE_PATH} && \
  einfo "Applied table:     "`cat ${VTABLE_PATH}`

  return $?
}


start() 
{
  ebegin "Changing CPU voltages table"

  if [ "$IS_CONFIGURED" = "yes" ]; then
    sysfs_check || return 1
    vtable_check ${CUSTOM_VTABLE} || return 1

    set_custom_table ${CUSTOM_VTABLE}
    eend $?
  else
    do_error "Custom voltage table is not configured. Check the file /etc/conf.d/undervolt"
  fi
}

# I think it is not necessary to switch to the default voltage table on shutdown
stop() 
{
  if [ "$SWITCH_BACK" = "yes" ]; then
    if [ "$IS_CONFIGURED" = "yes" ]; then
      ebegin "Switching back to default CPU voltage table"

      sysfs_check || return 1
      vtable_check ${DEFAULT_VTABLE} || return 1

      set_custom_table ${DEFAULT_VTABLE}
      eend $?
    else
      do_error "Default voltage table is not configured. Check the file /etc/conf.d/undervolt"
    fi
  else
    ebegin "Not switching back to default CPU voltage table (disabled in configuration)"
    eend 0
  fi 
}

At first I got a message 
./undervolt: /sbin/runscript: bad interpreter: No such file or directory  

So I installed minicom, changed the interpreter to /usr/bin/runscript, and now I get that the command 'depend' is unknown. Is it not possible to run these scripts in Ubuntu? I understand that script comes from Gentoo Linux. What am I doing wrong? Thanks

---

### Post by dcstar on 2006-02-17
[QUOTE=konradsa]Hi, I have the following script I am trying to execute in Ubuntu 5.10. I already patched and installed a kernel that allows undervolting. Now I would like to automatically apply my new voltages at startup with the following script:

#!/sbin/**runscript**
# Copyright 1999-2005 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: $
......
At first I got a message 
./undervolt: **/sbin/runscript: bad interpreter**: No such file or directory  

So I installed minicom, changed the interpreter to /usr/bin/runscript, and now I get that the command 'depend' is unknown. Is it not possible to run these scripts in Ubuntu? I understand that script comes from Gentoo Linux. What am I doing wrong? Thanks[/QUOTE]
Using a Gentoo script.

There is no such thing as "runscript" in Ubuntu.

---

### Post by konradsa on 2006-02-17
Ok,

So that means there is no way I can use that in Ubuntu. Can I translate it to some other scripting language?

-- Sascha

---

