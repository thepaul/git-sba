=======
git-sba
=======

This script is meant to be aliased as a git command, i.e.::

    sba = "!path/to/git-sba"

in the ``[alias]`` section of `.gitconfig`_.

It delivers a view like ``git show-branch -a``, but differs in a couple ways:

1. Only remote branches named the same as your local branches will be
   shown. This can simplify the view when your main object is to compare
   your local branches with relevant remote branches.

2. The results are shown with your git pager (unclear why ``git show-branch``
   doesn't already do this)

A couple extra options in your git config can tune this behavior:

sba.hide
    This should be a semicolon-separated list of patterns naming local or
    remote branches that you don't want to see in the sba output. For
    example, I have a branch named "public" corresponding to public
    releases which sometimes lags far behind my other branches, and I
    normally don't care how it compares to them. I might set::

        $ git config sba.hide public

    (as a repo-specific setting) so it didn't clutter up the listing too
    much.

    Patterns in the ``sba.hide`` list can contain shell-style wildcards
    like ``*``, ``?``, and ``[abc]``.

sba.alwaysshow
    This should be a semicolon-separated list of patterns naming remote
    branches that you always want to see in the sba output, even if there
    are no corresponding local branches.

    Patterns in the ``sba.alwaysshow`` list can contain shell-style wildcards
    like ``*``, ``?``, and ``[abc]``.

.. _`.gitconfig`: http://www.kernel.org/pub/software/scm/git/docs/git-config.html
