= ABOUT CHEF FAT INSTALLER

 * Uses rvm, see http://rvm.beginrescueend.com
 * Installs chef-client, Ruby, and gems in a self-contained distribution
 * For limited support contact the author of this distribution.

= USAGE NOTES

1. Checkout architecture-specific branch.

  git checkout i386
  git checkout x86_64

2. Run build script, which should output a makeself .run file

  ./build-installer

The makeself directory contains the makeself files necessary to build the .run file

The buildroot directory contains the files and installer script.  Everything
in this directory, buildroot, gets rolled up into the FAT installer.

== INSTALLATION

1. Simply execute the chef-fat-installer.i386.run, or chef-fat-installer.x86_64.run.

== WARNINGS

=== PERTINENT TO RVM

Chances are this deployment could be destructive to an existing rvm environment.
It shouldn't overwrite the default location of /usr/local/rvm, instead it installs
in /opt/chef.  However, the installer could override your default rvm installation.

I kept the installation in an alternate location to avoid conflict with default rvm
directory.  Files, and directories of interest.  If you have an existing rvm
installation, this distribution is not recommended for that machine.

 * /opt/chef - Installation path
 * /etc/rvm.sh - Profile script
 * /etc/rvmrc - exports rvm path for Chef

=== INIT.D SCRIPTS

The init scripts shipped with the Chef fat installer need to
source /etc/profile.d/rvm.sh to have the proper PATH environment variables to work
with Chef.  If your chef::client_service recipe overwrites the init scripts, then
consider adding the following code snippet to your init cookbook_file.

if [ -x /etc/profile.d/rvm.sh ]; then
  . /etc/profile.d/rvm.sh
fi

= BUGS / FIXES

Pull requests welcome via github.

== WEBSITE

https://github.com/atomic-penguin/chef-fat-installer