---
title: "dpkg -l help"
date: 2010-09-07
forum: General Help
---

### Post by COKEDUDE on 2010-09-07
I did the command "dpkg -l" and I noticed next to certain packages it said "ii" and "rc". What does "ii" and "rc" mean? Below is an example of what I saw. 

ii  whois                                 5.0.0ubuntu3                          
          an intelligent whois client
rc  wicd-daemon                           1.7.0+ds1-2                           
          wired and wireless network manager - daemon

---

### Post by sisco311 on 2010-09-07
The  first  three columns of the output show the desired action, the package status, and errors, in that order.

Check out the man page for details:
```
man dpkg-query
```

---

### Post by COKEDUDE on 2010-09-07
> **sisco311 said:**
> The  first  three columns of the output show the desired action, the package status, and errors, in that order.

Check out the man page for details:
```
man dpkg-query
```

You must have better man pages than me. I don't have "ii" or "rc" in my man pages.

---

### Post by sisco311 on 2010-09-07
> **cokedude said:**
> you must have better man pages than me. I don't have "ii" or "rc" in my man pages.

OKAY.

```

dpkg-query(1)                     dpkg suite                     dpkg-query(1)



name
       dpkg-query - a tool to query the dpkg database

synopsis
       dpkg-query [option...] command

description
       dpkg-query  is  a tool to show information about packages listed in the
       dpkg database.

Commands
       -l, --list package-name-pattern...
              List packages matching given pattern. If no package-name-pattern
              is  given,  list all packages in /var/lib/dpkg/status, excluding
              the ones marked as not-installed (i.e.  Those  which  have  been
              previously  purged). Normal shell wildchars are allowed in pack&#8208;
              age-name-pattern. Please note you will probably  have  to  quote
              package-name-pattern  to prevent the shell from performing file&#8208;
              name expansion. For example this will  list  all  package  names
              starting with “libc6”:

                Dpkg-query -l 'libc6*'

         [B]     the  first  three columns of the output show the desired action,
              the package status, and errors, in that order.[/B]

              Desired action:
                U = unknown
                i = install
                h = hold
                r = remove
                p = purge

              package status:
                N = not-installed
                c = config-files
                h = half-installed
                u = unpacked
                f = half-configured
                w = triggers-awaiting
                t = triggers-pending
                i = installed

              error flags:
                <empty> = (none)
                r = reinst-required

              an uppercase status or error letter  indicates  the  package  is
              likely  to  cause  severe  problems. Please refer to dpkg(1) for
              information about the above states and flags.

              The output format of this option is not configurable, but varies
              automatically  to  fit  the  terminal  width. It is intended for
              human readers,  and  is  not  easily  machine-readable.  See  -w
              (--show) and --showformat for a way to configure the output for&#8208;
              mat.

       -w, --show package-name-pattern...
              Just like the --list option this will list all packages matching
              the  given  pattern.  However the output can be customized using
              the --showformat option.  The default output  format  gives  one
              line  per  matching  package,  each  line  having  the  name and
              installed version of the package, separated by a tab.

       -s, --status package-name...
              Report status of specified package. This just displays the entry
              in the installed package status database.

       -l, --listfiles package-name...
              List files installed to your system from package-name.  However,
              note that files created by package-specific installation-scripts
              are not listed.

       -c, --control-path package-name [control-file]
              list paths for control files installed to your system from pack&#8208;
              age-name.  If control-file is specified then only list the  path
              for that control file if it is present. Warning: This command is
              semi-public, it should be used only as a last  resort  solution,
              and  if no other interface is available. It might get deprecated
              later on if better interfaces or the current architectural defi&#8208;
              ciencies have been solved.

       -s, --search filename-search-pattern...
              Search  for  a  filename  from  installed packages. All standard
              shell wildchars can be used in the pattern.  This  command  will
              not  list extra files created by maintainer scripts, nor will it
              list alternatives.

       -p, --print-avail package-name...
              Display   details    about    package-name,    as    found    in
              /var/lib/dpkg/available. Users of apt-based frontends should use
              apt-cache show package-name instead as  the  available  file  is
              only kept up-to-date when using dselect.

       -h, --help
              show the usage message and exit.

       --version
              show the version and exit.

Options
       --admindir=dir
              change  the  location of the dpkg database. The default location
              is /var/lib/dpkg.

       -f, --showformat=format
              this option is used to specify the format of the  output  --show
              will  produce.  The  format  is a string that will be output for
              each package listed.

              In the format string, “\” introduces escapes:

                  \n  newline
                  \r  carriage return
                  \t  tab

              “\” before any other character suppresses any special meaning of
              the following character, which is useful for “\” and “$”.

              Package information can be included by inserting variable refer&#8208;
              ences to package fields  using  the  syntax  “${field[;width]}”.
              Fields are printed right-aligned unless the width is negative in
              which case left alignment will be used. The following fields are
              recognised  but they are not necessarily available in the status
              file (only internal fields or fields stored in the binary  pack&#8208;
              age end up in it):

                  Architecture
                  bugs
                  conffiles (internal)
                  config-version (internal)
                  conflicts
                  breaks
                  depends
                  description
                  enhances
                  essential
                  filename (internal, dselect related)
                  homepage
                  installed-size
                  md5sum (internal, dselect related)
                  msdos-filename (internal, dselect related)
                  maintainer
                  origin
                  package
                  pre-depends
                  priority
                  provides
                  recommends
                  replaces
                  revision (obsolete)
                  section
                  size (internal, dselect related)
                  source
                  status (internal)
                  suggests
                  tag (usually not in the .deb but in apt's packages files)
                  triggers-awaited (internal)
                  triggers-pending (internal)
                  version

              the  default format string is “${package}\t${version}\n”.  Actu&#8208;
              ally, all other fields found  in  the  status  file  (i.e.  User
              defined  fields) can be requested, too. They will be printed as-
              is, though, no conversion nor error checking is  done  on  them.
              To  get  the  name of the dpkg maintainer and the installed ver&#8208;
              sion, you could run:

                Dpkg-query -w -f='${package} ${version}\t${maintainer}\n' dpkg

exit status
       0      the requested query was successfully performed.

       1      problems were encountered while parsing the command line or per&#8208;
              forming  the  query,  including  no  file or package being found
              (except for --control-path).

Environment
       columns
              this setting influences the  output  of  the  --list  option  by
              changing the width of its output.

Author
       copyright © 2001 wichert akkerman

       this  is free software; see the gnu general public licence version 2 or
       later for copying conditions. There is no warranty.

See also
       dpkg(1).




Debian project                    2010-03-07                     dpkg-query(1)
```

---

### Post by djeikyb on 2010-12-23
^ Thanks for that. I don't have that information in man dpkg or man dpkg-query.

---

