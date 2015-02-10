1.1 Getting Started - About Version Control

About Version COntrol
  Version control is a system that records changes to a file or set of files over time so that you can recall specific versions
  later. Note that any type of file on a computer can be placed uncer a version control.
  
  VCS allows you to revert files back to a previous state, revert the entire project back to a previous state, review changes 
  made over time, see who last modified something that may cause a problem, who introduced an issue and when, and more. Using
  VCS also means that if you screw things up or lose files, you can generally recover easily.
  
Local Version Control Systems
  Many people's version-contrl method of choice is to copy files into another directory. This approach is very common because
  it is so simple, but it is also incredibly error prone. 
  
  One of the more popular VCS tools was a system called rcs, which is still distributed with many computers today. One of the 
  more popular VCS tools was a system called rcs, which is still distributed with many computers today. This tool basically 
  works by keeping patch sets from one revision to another in a special format on disk. It can then recreate what any file 
  looked like at any point in time by adding up all the patches.
  
Distributed Version Control Systems
  This is where Distributed Version Control Systems (DVCSs) step in. In a DVCS, clients don’t just check out the latest snapshot 
  of the files. They fully mirror the repository. Thus if any server dies, and these systems were collaborating via it, any of 
  the client repositories can be copied back up to the server to restore it. Every checkout is really a full backup of all the 
  data.

  Many of these systems deal pretty well with having several remote repositories they can work with. So you can collaborate with 
  different groups of people in different ways simultaneously within the same project.

1.2 Getting Startted - A Short History of Git

A Short History of Git
  Git began with a bit of creative destruction and fiery controversy. The Linux kernel is an open source software project of fairly 
  large scope. For most of the lifetime of the Linux kernel maintenance, changes to the software were passed around as patches and 
  archived files. In 2002, the Linux kernel project began using a proprietary DVCS system called BitKeeper.
  
  In 2005, the relationship between the community that developed the Linux kernel and the commercial company that developed BitKeeper 
  broke down, and the tool’s free-of-charge status was revoked. This prompted the Linux development community to develop their own 
  tool based on some of the lessons they learned while using BitKeeper. Some of the goals of the new system were as follows:
   - Speed
   - Simple design
   - Strong support for non-linear development
   - Fully distributed
   - Able to handle large projects like the Linux kernel effeciently
  Since its birth in 2005, Git has evolved and matured to be easy to use and yet retain these initial qualities. It’s incredibly fast, 
  it’s very efficient with large projects, and it has an incredible branching system for non-linear development
  
1.3 Getting Started - Git Basics

Git Basics
  This is an important section to absorb to know the fundamentals of Git and how it works so that you can use Git effectively and efficiently.
  Git stores and think about information differently than the other VCSs such as Subversion and Perforce. Understanding the differences
  will help prevent you from becoming confused while using it.

Snapshots, Not Differences
  The major difference between Git and any other VCS is the way Git thinks about its data. Most other systems store information as a list of 
  file-based changes. 
  
  Git doesn’t think of or store its data this way. Instead, Git thinks of its data more like a set of snapshots of a mini filesystem. Every 
  time you commit, or save the state of your project in Git, it basically takes a picture of what all your files look like at that moment 
  and stores a reference to that snapshot. To be efficient, if files have not changed, Git doesn’t store the file again—just a link to the 
  previous identical file it has already stored.
  
Nearly Every Operation Is Local
  Most operations in Git only need local files and resources to operate — generally no information is needed from another computer on your 
  network.

Git Has Integrity
  Everything in Git is check-summed before it is stored and is then referred to by that checksum. This means it’s impossible to change the 
  contents of any file or directory without Git knowing about it. This functionality is built into Git at the lowest levels and is integral 
  to its philosophy. You can’t lose information in transit or get file corruption without Git being able to detect it.
  
  You will see these hash values all over the place in Git because it uses them so much. Git stores everything not by file name but in the 
  Git database addressable by the hash value of its contents.
  
Git generally Only Adds Data
  When you do actions in Git, nearly all of them only add data to the Git database. It is very difficult to get the system to do anything 
  that is not undoable or to make it erase data in any way. But after you commit a snapshot into Git, it is very difficult to lose, especially 
  if you regularly push your database to another repository.
  
The Three States
  Git has three main states that your files can reside in: committed, modified, and staged. Committed means that the data is safely stored in 
  your local database. Modified means that you have changed the file but have not committed it to your database yet. Staged means that you have 
  marked a modified file in its current version to go into your next commit snapshot.
  
  Git directory is where Gits stores the metadata and object database for your project. This is the most important part of Git, and it is what 
  is copied when you clone a repository from another computer.
  
  The working directory is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git 
  directory and placed on disk for you to use or modify.
  
  The basic Git workflow goes something like this:
   - You modify files in your working directory.
   - You stage the files, adding snapshots of them to your staging area.
   - You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.
   
  If a particular version of a file is in the Git directory, it’s considered committed. If it’s modified but has been added to the staging area, 
  it is staged. And if it was changed since it was checked out but has not been staged, it is modified.
  
1.4 Getting Started - The Command Line

The Command Line
   The command line is the only place you can run all Git commands – most of the GUIs only implement some subset of Git functionality for simplicity. 
   If you know how to run the command line version, you can probably also figure out how to run the GUI version, while the opposite is not necessarily true.
   
1.5 Getting Started - Installing Git

Installing Git
  Before you start using Git, you have to make it available on your computer. Even if it’s already installed, it’s probably a good idea to update to the 
  latest version. You can either install it as a package or via another installer, or download the source code and compile it yourself.
  
Installing on Linux
  There are instructions for installing on several different Unix flavors on the Git website, at http://git-scm.com/download/linux.
  
Installing on Mac
  There are several ways to install Git on a Mac. The easiest is probably to install the Xcode Command Line Tools.
  
   You can also install it via a binary installer. An OSX Git installer is maintained and available for download 
   at the Git website, at http://git-scm.com/download/mac.
   
   You can also install it as part of the GitHub for Mac install. Their GUI Git tool has an option to install command line tools as well. You can download 
   that tool from the GitHub for Mac website, at http://mac.github.com.

Installing on Windows
  There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to http://git-scm.com/download/win 
  and the download will start automatically. Note that this is a project called Git for Windows (also called msysGit), which is separate from Git itself; for more 
  information on it, go to http://msysgit.github.io/.

Installing from Source
  If you do want to install Git from source, you need to have the following libraries that Git depends on: curl, zlib, openssl, expat, and libiconv. You may refer to 
  http://git-scm.com/book/en/v2/Getting-Started-Installing-Git for further details.
  
1.6 Getting Started - First-Time Git Setup

First-Time Git Setup
  Git comes with a tool called git config that lets you get and set configuration variables that control all aspects of how Git looks and operates. These variables 
  can be stored in three different places:
   - /etc/gitconfig file: Contains values for every user on the system and all their repositories. If you pass the option --system to git config, it reads and writes 
     from this file specifically.
   - ~/.gitconfig or ~/.config/git/config file: Specific to your user. You can make Git read and write to this file specifically by passing the --global option.
   - config file in the Git directory (that is, .git/config) of whatever repository you’re currently using: Specific to that single repository.

  Each level overrides values in the previous level, so values in .git/config trump those in /etc/gitconfig.

  On Windows systems, Git looks for the .gitconfig file in the $HOME directory (C:\Users\$USER for most people). It also still looks for /etc/gitconfig, although 
  it’s relative to the MSys root, which is wherever you decide to install Git on your Windows system when you run the installer.
  
Your Identity
  $ git config --global user.name "rmbpascual"
  $ git config --global user.email pasacualrizamae@gmail.com

Your Editor
  $ git config --global core.editor gedit
  
Checking Your Settings
  $ git config --list
  user.name=rmbpascual
  user.email=pascualrizamae@gmail.com
  core.editor=gedit
  merge.tool=vimdiff
  core.repositoryformatversion=0
  core.bare=false
  core.logallrefupdates=true
  
  $ git config user.name
  rmbpascual
  
1.7 Getting Started - Getting Help

Getting Help
  $ git help config
  
1.8 Getting Started - Summary

Summary
  You should have a basic understanding of what Git is and how it’s different from the centralized version control system you may have previously been using. You 
  should also now have a working version of Git on your system that’s set up with your personal identity. It’s now time to learn some Git basics.
