# LiveConfig Learn Spam
SpamAssassin learning script for LiveConfig enabled web-hosting systems

## SpamAssassin
You are able to enable SpamAssassin when using a LiveConfig installation on your system. SpamAssassin is only running effectively when it gets "trained" with spam message. It will improve its detection algorithm and this will result in a higher detection rate.

To do so you may use the `sa-learn` command provided by SpamAssassin. To tell SpamAssassin to learn a single message (or even a whole folder) as spam (or as ham = no spam) you may provide a directory or pipe a message

`sa-learn --spam /path/to/spam/directory` or `cat bad_message.eml | sa-learn --spam`

To do the same with ham messages you can use the `--ham` argument instead of `--spam`.

## LiveConfig
LiveConfig stores all messages of its users in `/var/mail`. The learning script just utilizes the `find` command to get the absolute paths of all `.Spam` and `.Junk` directories of all mail users. Those paths are passed to `sa-learn` to train SpamAssassin.

## Setup
1. Make sure SpamAssassin is fully enabled and working on your system.
2. Place the `spamassassin-learn` script anywhere on your system (e.g. `/usr/bin/adm/spamassassin-learn`)
3. Execute the script every day or even every few hours and pipe its output to `/dev/null` (using ` > /dev/null 2>&1`)
4. Profit.
