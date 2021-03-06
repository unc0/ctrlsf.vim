# ctrlsf.vim

An ack/ag powered code search and view tool, in an intuitive way with fairly more context.

![ctrlsf demo](http://i.imgur.com/HOK9llj.gif)

## Installation

1. Make sure you have installed [ack][1] or [ag][2].
2. An easy way to install CtrlSF is using a package manager, like [pathogen][3], [vundle][4] or [neobundle][5].

    In vundle:

    ```vim
    Bundle 'dyng/ctrlsf.vim'
    ```

3. Read *Basic Usage* for more.

## Basic Usage

1. Run `:CtrlSF [pattern]`, it will split a new window to show search result.
2. Press `Enter` if you wanna jump to that file, or press `q` to quit.
3. Run `:CtrlSFOpen` can reopen CtrlSF window if you are interested in other matches. It is costless because it won't invoke a same but new search.
4. You can pass arguments like `-i`, `-C` or path directly to ack/ag backend in `:CtrlSF` command.

    ```vim
    CtrlSF -i -C 1 [pattern] /restrict/to/some/path
    ```

## Configuration

- `g:ctrlsf_ackprg` defines the external ack-like program which CtrlSF uses as source. If nothing is specified, CtrlSF will try *ag* first and fallback to *ack* if *ag* is not available. You can also explicitly define it by

    ```vim
    let g:ctrlsf_ackprg = 'ag'
    ```

- `g:ctrlsf_auto_close` defines the behavior of CtrlSF window after you press the `Enter`. By default CtrlSF window will automatically be closed if you jump to some file, you can prevent it by set `g:ctrlsf_auto_close` to 0.

    ```vim
    let g:ctrlsf_auto_close = 0
    ```

- `g:ctrlsf_context` defines how to print lines around the matching line (refer to `ack`'s [manual][6]). It is default to be `-C 3`, you can overwrite it by

    ```vim
    let g:ctrlsf_context = '-B 5 -A 3'
    ```

A full document about options can be found in `:help ctrlsf-options`.

## Why not ack.vim or ag.vim ?
1. ack.vim depends on vim's builtin `:grep` command, which you can not change the output format. What makes me to write this plugin is that I found reading lines with no highlight and no context is totally a pain. (Use of `:cnext` and `:cprevious` can relieve it, yes.)
2. Fixed misescape in ack.vim (and also ag.vim), it lets you can use literal '#' and '%' without annoying escape now. For more information, read [manual][7] of ack.vim.
3. ag.vim is actually a fork of ack.vim with minor change.

[1]: https://github.com/petdance/ack
[2]: https://github.com/ggreer/the_silver_searcher
[3]: https://github.com/tpope/vim-pathogen
[4]: https://github.com/gmarik/vundle
[5]: https://github.com/Shougo/neobundle.vim
[6]: http://search.cpan.org/~petdance/ack-2.12/ack#OPTIONS
[7]: https://github.com/mileszs/ack.vim#gotchas
