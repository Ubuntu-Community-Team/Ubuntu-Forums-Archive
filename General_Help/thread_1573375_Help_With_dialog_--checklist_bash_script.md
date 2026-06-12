---
title: "Help With: dialog --checklist bash script"
date: 2010-09-12
forum: General Help
---

### Post by _KE1HA_ on 2010-09-12
If this is not the right place, please move to appropriate forum.

Hello all,

I'm working on a series of scripts to download ISO's from the command line using dialog. When the user makes his/her selections, the output file is working as expected, however, if they return to the selection menu, the default selections are restored ( this is normal behavior, as if comes from the static default-cfg file ). This is what I'm trying to change as I would like to have the menu, upon returning, be defaulted back to their previous selections.

I asked in the Bash IRC channel, and gerha was kind enough to provide me with an awk string, however, it's not updating the the user config file as needed:

Final Version Made into a Function Now:
```

ubuntu_config(){ #---ubuntu download configuraiton page

UBCFGFILE="${CONFIG}/ubuntu-cfg"

test_null(){ #---test config file is not null
 if [[ ! -f $UBCFGFILE ]]; then
  touch ${CONFIG}/ubuntu-cfg
  cat ${CONFIG}/ubuntu-orig > ${CONFIG}/ubuntu-cfg

  elif [[ `ls -l $UBCFGFILE | awk '{print $5}'` -eq 0 ]]; then
   cat ${CONFIG}/ubuntu-orig > ${CONFIG}/ubuntu-cfg
 fi    
}

update_cfg(){ #---update user-cfg after selections

#--- Gier Houge Hack : gierha@caracal.stud.ntnu.no  update user-cfg selections
 awk 'NR==FNR {selected[$1]=1;next}{if ($1 in selected) \
 print $1,"\"\"","on","\\"; else print $1,$2,"off","\\"}' \
 ${CONFIG}/ubuntu-selections ${UBCFGFILE} >> ./temp-file
 mv ./temp-file ${UBCFGFILE}
}

# --- begin main script
 while [ 0 ]; do

#---check if ubuntu-cfg, if null value, add template
 test_null

#--- present selection options
 dialog --backtitle "${BACKT} ${VERSION}" --title "${UBCONFIGMSG}" --ok-label \
        SAVE --nocancel --separate-output --checklist "${SELECTISOMSG}" 16 60 14 \
        --file $UBCFGFILE 2> ${CONFIG}/ubuntu-selections

#---update the config menu with user selections
 update_cfg

 break
done
}

```
> 
awk 'NR==FNR {selected[$1]=1;next}{if ($1 in selected) print $1,"\"\"","on","\\"; else print $1,$2,"off","\\"}' test.txt ./user-cfg >> ./temp-file
mv ./temp-file ./user-cfg


---

