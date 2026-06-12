---
title: "ZSh config error after upgrade"
date: 2010-04-07
forum: General Help
---

### Post by fhsm on 2010-04-07
My .zshrc and .zsh/functions/prompt_fhsm_setup have been the same for a long time. I recently upgraded from Hardy to 9.10 and have started having a problem with my prompt. The error is:
[I]prompt_fhsm_setup:32: bad math expression: illegal character: \
[/I]

I think the line referenced is:*prompt_gfx_hyphen=$'\xe2\x94\x80'* but that doesn't seem like a likely cause. 

Here's the whole file ```

# fhsm prompt theme

prompt_fhsm_help () {
  cat <<'EOF'
This prompt is color-scheme-able.  You can invoke it with:

  prompt fhsm [ 8bit ] [<color1> [<color2> [<color3>] [<color4>] [<color5>]]

where the colors are for the hyphens, current directory, user,
host and user input respectively.  The default colors are cyan, green,
magenta, blue and white.  This theme requires a dark background.

If you have either UTF-8 or the `nexus' or `vga' console fonts or similar,
you can specify the `8bit' option to use 8-bit replacements for the
7-bit characters.

This is a rip off of the adam2 theme.

EOF
}

prompt_fhsm_setup () {
  # Some can't be local
  local prompt_gfx_tlc prompt_gfx_mlc prompt_gfx_blc

  if [[ $1 == '8bit' ]]; then
    shift
    if [[ ${LC_ALL:-${LC_CTYPE:-$LANG}} = *UTF-8* ]]; then
      prompt_gfx_tlc=$'\xe2\x94\x8c'
      prompt_gfx_mlc=$'\xe2\x94\x9c'
      prompt_gfx_blc=$'\xe2\x94\x94'
      prompt_gfx_hyphen=$'\xe2\x94\x80'
    else
      prompt_gfx_tlc=$'\xda'
      prompt_gfx_mlc=$'\xc3'
      prompt_gfx_blc=$'\xc0'
      prompt_gfx_hyphen=$'\xc4'
    fi
  else
    prompt_gfx_tlc='.'
    prompt_gfx_mlc='|'
    prompt_gfx_blc='\`'
    prompt_gfx_hyphen='-'
  fi

  # Default color scheme
  prompt_fhsm_color1=${1:-'cyan'}    # hyphens
  prompt_fhsm_color2=${2:-'green'}   # current directory
  prompt_fhsm_color3=${3:-'magenta'} # user@
  prompt_fhsm_color4=${4:-'blue'}    # host
  prompt_fhsm_color5=${5:-'white'}   # user input

  local prompt_gfx_bbox 
  prompt_gfx_tbox="%{$fg_bold[$prompt_fhsm_color1]%}${prompt_gfx_tlc}%{$fg_no_bold[$prompt_fhsm_color1]%}${prompt_gfx_hyphen}"
  prompt_gfx_bbox="%{$fg_bold[$prompt_fhsm_color1]%}${prompt_gfx_blc}${prompt_gfx_hyphen}%{$fg_no_bold[$prompt_fhsm_color1]%}"

  # This is a cute hack.  Well I like it, anyway.
  prompt_gfx_bbox_to_mbox=$'%{\e[A\r'"$fg_bold[$prompt_fhsm_color1]${prompt_gfx_mlc}$fg_no_bold[$prompt_fhsm_color1]${prompt_gfx_hyphen}"$'\e[B%}'

  prompt_l_paren="%{$fg_bold[grey]%}("
  prompt_r_paren="%{$fg_bold[grey]%})"

  prompt_user_host="%{$fg_bold[$prompt_fhsm_color4]%}%n%{$fg_no_bold[$prompt_fhsm_color4]%}@%{$fg_no_bold[$prompt_fhsm_color3]%}%m"

  prompt_line_1a="$prompt_gfx_tbox$prompt_l_paren%{$fg_bold[$prompt_fhsm_color2]%}%~$prompt_r_paren%{$fg_no_bold[$prompt_fhsm_color1]%}"
  prompt_line_1b="$prompt_l_paren$prompt_user_host$prompt_r_paren%{$fg_no_bold[$prompt_fhsm_color1]%}${prompt_gfx_hyphen}"

  prompt_line_2="$prompt_gfx_bbox${prompt_gfx_hyphen}%{$fg_bold[white]%}"

  prompt_char="%(!.#.>)"

  precmd () { prompt_fhsm_precmd; setopt promptsubst }
  preexec () { prompt_fhsm_preexec }
}

prompt_fhsm_precmd () {
  setopt noxtrace localoptions extendedglob
  local prompt_line_1

  prompt_fhsm_choose_prompt

  PS1="$prompt_line_1$prompt_newline$prompt_line_2%{$fg_bold[white]%}$prompt_char %{$fg_bold[$prompt_fhsm_color5]%}"
  PS2="$prompt_line_2%{$prompt_gfx_bbox_to_mbox$fg_bold[white]%}%_> %{$fg_bold[$prompt_fhsm_color5]%}"
  PS3="$prompt_line_2%{$prompt_gfx_bbox_to_mbox$fg_bold[white]%}?# %{$fg_bold[$prompt_fhsm_color5]%}"
  RPS1=$'%{\e[1;30m%}<%T%{\e[0m%}%(?..%{\e[0;31m%} %?%{\e[0m%})' 
      #this is a bit unclear but the %{ %} is tells zsh not to count those chars into the prompt length, ie escape seq.
      #then the \e[...m part is a color seqence, \e[0m is the color reset seqence
      #%T is just expanded to the time
      #Next is a test for the exit code of the previous command using %?
      #This test uses the %([char].[true str].[false str]) construct to test for non zero exit codes
      #Zero exit codes print nothing because the true str is blank, the .., but the false string prints the exit code in red
}

prompt_fhsm_choose_prompt () {
  local prompt_line_1a_width=${#${(S%%)prompt_line_1a//\%\{*\%\}}}
  local prompt_line_1b_width=${#${(S%%)prompt_line_1b//\%\{*\%\}}}

  local prompt_padding_size=$(( COLUMNS
                                  - prompt_line_1a_width
                                  - prompt_line_1b_width ))

  # Try to fit in long path and user@host.
  if (( prompt_padding_size > 0 )); then
    local prompt_padding
    eval "prompt_padding=\${(l:${prompt_padding_size}::${prompt_gfx_hyphen}:)_empty_zz}"
    prompt_line_1="$prompt_line_1a$prompt_padding$prompt_line_1b"
    return
  fi

  prompt_padding_size=$(( COLUMNS - prompt_line_1a_width ))

  # Didn't fit; try to fit in just long path.
  if (( prompt_padding_size > 0 )); then
    local prompt_padding
    eval "prompt_padding=\${(l:${prompt_padding_size}::${prompt_gfx_hyphen}:)_empty_zz}"
    prompt_line_1="$prompt_line_1a$prompt_padding"
    return
  fi

  # Still didn't fit; truncate 
  local prompt_pwd_size=$(( COLUMNS - 5 ))
  prompt_line_1="$prompt_gfx_tbox$prompt_l_paren%{$fg_bold[$prompt_fhsm_color2]%}%$prompt_pwd_size<...<%~%<<$prompt_r_paren%{$fg_no_bold[$prompt_fhsm_color1]$prompt_gfx_hyphen%}"
}

prompt_fhsm_preexec () {
  print -n "$reset_color"
}

prompt_fhsm_setup "$@"
```

Any ideas?

---

### Post by cricketer1234 on 2010-04-08
Certament, sembla ser que el tema va per aquí, Lluís, que els teclats i tots els dispositius d'entrada de dades han heredat la disposició de les màquines antigues, i els fabricants de telèfons van creure que anava millor la seva disposició per marcar. Coses de la vida :smile:

---

### Post by fhsm on 2010-04-08
> **cricketer1234 said:**
> Certament, sembla ser que el tema va per aquí, Lluís, que els teclats i tots els dispositius d'entrada de dades han heredat la disposició de les màquines antigues, i els fabricants de telèfons van creure que anava millor la seva disposició per marcar. Coses de la vida :smile:

[QUOTE=Google_Translate]Certainly, it seems that the issue was there, Lluís, keypads and all input devices have inherited the disposal of old machines, and phone manufacturers thought they were better at your disposal to make. Things in life[/QUOTE]

Anyone have something else to offer?

---

### Post by fhsm on 2010-04-09
So this seems to have something to do with UTF-8. Does this seem reasonable to those who know more?

The referenced line (line 32) can be changed around without any impact on the error. 

The whole file is up at: [http://pastebin.com/esFLnMML](http://pastebin.com/esFLnMML)

Anyone got any ideas?

---

### Post by fhsm on 2010-11-30
Stumbled across the answer elsewhere. Thought I'd update the post for future googlers.

Note the switch to %B%F to format bold.

```

# fhsm prompt theme

prompt_fhsm_help () {
  cat <<'EOF'
This prompt is color-scheme-able.  You can invoke it with:

  prompt fhsm [ 8bit ] [<color1> [<color2> [<color3>] [<color4>] [<color5>]]

where the colors are for the hyphens, current directory, user,
host and user input respectively.  The default colors are cyan, green,
magenta, blue and white.  This theme requires a dark background.

If you have either UTF-8 or the `nexus' or `vga' console fonts or similar,
you can specify the `8bit' option to use 8-bit replacements for the
7-bit characters.

This is a rip off of the adam2 theme.
EOF
}

prompt_fhsm_setup () {
  # Some can't be local
  local prompt_gfx_tlc prompt_gfx_mlc prompt_gfx_blc

  if [[ $1 == '8bit' ]]; then
    shift
    if [[ ${LC_ALL:-${LC_CTYPE:-$LANG}} = *UTF-8* ]]; then
      prompt_gfx_tlc=$'\xe2\x94\x8c'
      prompt_gfx_mlc=$'\xe2\x94\x9c'
      prompt_gfx_blc=$'\xe2\x94\x94'
      prompt_gfx_hyphen=$'\xe2\x94\x80'
    else
      prompt_gfx_tlc=$'\xda'
      prompt_gfx_mlc=$'\xc3'
      prompt_gfx_blc=$'\xc0'
      prompt_gfx_hyphen=$'\xc4'
    fi
  else
    prompt_gfx_tlc='.'
    prompt_gfx_mlc='|'
    prompt_gfx_blc='\`'
    prompt_gfx_hyphen='-'
  fi

  # Default color scheme
  prompt_fhsm_color1=${1:-'cyan'}    # hyphens
  prompt_fhsm_color2=${2:-'green'}   # current directory
  prompt_fhsm_color3=${3:-'magenta'} # user@
  prompt_fhsm_color4=${4:-'blue'}    # host
  prompt_fhsm_color5=${5:-'white'}   # user input

  local prompt_gfx_bbox
  prompt_gfx_tbox="%B%F{$prompt_fhsm_color1}${prompt_gfx_tlc}%b%F{$prompt_fhsm_color1}${prompt_gfx_hyphen}"
  prompt_gfx_bbox="%B%F{$prompt_fhsm_color1}${prompt_gfx_blc}${prompt_gfx_hyphen}%b%F{$prompt_fhsm_color1}"

  # This is a cute hack.  Well I like it, anyway.
  prompt_gfx_bbox_to_mbox=$'%{\e[A\r'"%}%B%F{$prompt_fhsm_color1}${prompt_gfx_mlc}%b%F{$prompt_fhsm_color1}${prompt_gfx_hyphen}%{"$'\e[B%}'

  prompt_l_paren="%B%F{grey}("
  prompt_r_paren="%B%F{grey})"

  prompt_user_host="%b%F{$prompt_fhsm_color4}%n%B%F{$prompt_fhsm_color4}@%b%F{$prompt_fhsm_color3}%m"

  prompt_line_1a="$prompt_gfx_tbox$prompt_l_paren%B%F{$prompt_fhsm_color2}%~$prompt_r_paren%b%F{$prompt_fhsm_color1}"
  prompt_line_1b="$prompt_l_paren$prompt_user_host$prompt_r_paren%b%F{$prompt_fhsm_color1}${prompt_gfx_hyphen}"

  prompt_line_2="$prompt_gfx_bbox${prompt_gfx_hyphen}%B%F{white}"
  
  prompt_char="%(!.#.>)"

  prompt_opts=(cr subst percent)
  
  add-zsh-hook precmd prompt_fhsm_precmd
}

prompt_fhsm_precmd () {
  setopt noxtrace localoptions extendedglob
  local prompt_line_1

  prompt_fhsm_choose_prompt
 %B%F
  PS1="$prompt_line_1$prompt_newline$prompt_line_2%B%F{white}$prompt_char %B%F{$prompt_fhsm_color5}"
  PS2="$prompt_line_2%{$prompt_gfx_bbox_to_mbox%B%F{white}%_> %B%F{$prompt_fhsm_color5}"
  PS3="$prompt_line_2%{$prompt_gfx_bbox_to_mbox$%B%F{white}?# %B%F{$prompt_fhsm_color5}"
  RPS1=$'%{\e[1;30m%}<%T%{\e[0m%}%(?..%{\e[0;31m%} %?%{\e[0m%})'
#  zle_highlight[(r)default:*]="default:fg=$prompt_fhsm_color4,bold"
    #this is a bit unclear but the %{ %} is tells zsh not to count those chars into the prompt length, ie escape seq.
    #then the \e[...m part is a color seqence, \e[0m is the color reset seqence
    #%T is just expanded to the time
    #Next is a test for the exit code of the previous command using %?
    #This test uses the %([char].[true str].[false str]) construct to test for non zero exit codes
    #Zero exit codes print nothing because the true str is blank, the .., but the false string prints the exit code in red
}

prompt_fhsm_choose_prompt () {
  local prompt_line_1a_width=${#${(S%%)prompt_line_1a//(\%([KF1]|)\{*\}|\%[Bbkf])}}
  local prompt_line_1b_width=${#${(S%%)prompt_line_1b//(\%([KF1]|)\{*\}|\%[Bbkf])}}

  local prompt_padding_size=$(( COLUMNS
                                  - prompt_line_1a_width
                                  - prompt_line_1b_width ))

  # Try to fit in long path and user@host.
  if (( prompt_padding_size > 0 )); then
    local prompt_padding
    eval "prompt_padding=\${(l:${prompt_padding_size}::${prompt_gfx_hyphen}:)_empty_zz}"
    prompt_line_1="$prompt_line_1a$prompt_padding$prompt_line_1b"
    return
  fi

  prompt_padding_size=$(( COLUMNS - prompt_line_1a_width ))

  # Didn't fit; try to fit in just long path.
  if (( prompt_padding_size > 0 )); then
    local prompt_padding
    eval "prompt_padding=\${(l:${prompt_padding_size}::${prompt_gfx_hyphen}:)_empty_zz}"
    prompt_line_1="$prompt_line_1a$prompt_padding"
    return
  fi

  # Still didn't fit; truncate
  local prompt_pwd_size=$(( COLUMNS - 5 ))
  prompt_line_1="$prompt_gfx_tbox$prompt_l_paren%B%F{$prompt_fhsm_color2}%$prompt_pwd_size<...<%~%<<$prompt_r_paren%b%F{$prompt_fhsm_color1}$prompt_gfx_hyphen"
}

prompt_fhsm_preexec () {
  print -n "$reset_color"
}

prompt_fhsm_setup "$@"


```

---

