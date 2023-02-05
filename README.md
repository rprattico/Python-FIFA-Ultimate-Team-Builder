# Python-FIFA-Ultimate-Team-Builder
The Ultimate Team Builder
Project Documentation
Background Information
FIFA Ultimate Team is a popular video game module from the FIFA video game
series. In this module, users can create their own Soccer teams of real life players and use
them in games against other users’ own teams. A squad is built by selecting a player for
each position one at a time. In order to ensure optimal “chemistry” between the players of
the squad, every player must be from the same geographical theme chosen by the user. A
geographical theme refers to nationality, league or club team. Thus, players must be from
the same country, play in the same league or play for the same club team to have optimal
chemistry. After having chosen the geographical theme, the user can choose to further filter
their team using a desired physical attribute, which equally refers to a physical trait as well
as how well a player can perform a skill, such as defending or passing. The game has a
database of ratings for each of these physical attributes for each player of the game. These
ratings come from statistical analysis of the player’s real life capabilities of the skill. For
example, a player’s passing rating is created from the actual amount of passes he
completed throughout the prior season, his number of assists and other statistics related to
passing. As a result, the ratings for each skill is a realistic representation of the player’s
abilities in that skill. In addition, an average of all these ratings is taken for an overall score to
reflect the player’s overall quality. For instance, the game’s best player, Lionel Messi, has an
overall score of 94 on 100, which accurately represents his distinct quality over all other
players in real life. As previously mentioned, the user can choose to filter a team using a
desired attribute. If he chooses to do so, the players with the highest or lowest rating (as
decided by the user) in that attribute are placed on the team. If an attribute is not specified,
the players’ overall score is used. Moreover, because of the evolution of the game, there are
a variety of team formations. While all these formations have 11 players, each formation may
have a different number of each position. For example, a 5-3-2 formation will have 3
center-backs (CB), whereas a 4-4-2 will have 2. To simplify the construction of the team, the
program automatically uses a 4-3-3 formation (which is popularly used in both the video
game and in real life) for every team it builds.


Dozens of leagues exist around the world and hundreds of players play in each of
those leagues. To facilitate data storage, this program has refined the data down to only the
top 5 European leagues and the teams and players playing in those leagues. Furthermore,
this program is intended for the FIFA 16 edition of FIFA Ultimate Team, therefore the data
used in this program was recorded during the 2016 season. Since then, players and teams
of each league may have changed. The player ratings have also undoubtedly changed.
Hence, this program is only practical for the FIFA 16 instalment of FIFA Ultimate Team.


User’s Manual


1. Introduction
A version of the Ultimate Team module exists in nearly every sport themed video
game manufactured by EA Sports. This program can be applied to the Football, Hockey,
Basketball and Baseball versions of Ultimate Team, which is why you have a choice of
sports to choose from at the start of the program. However, due to the lack of data for all
other sports, you are limited to choosing “Soccer”. This is the only prompt that is not case
sensitive. In all other prompts, you must strictly input “yes”, “no”, or one of the suggested
answers without adding another character or space at the end.
2. The Template
After answering the first prompt, a list of the positions of the sport will appear as well
the formation being used. You can use this as a template to fill in with the players outputted
by the program at the end of the session.
3. The Geographical Theme
The next step is to select the geographical theme, which is necessary to ensure
optimal chemistry in your squad. A prompt will ask if you wish to see the directory from which
you can choose the theme, answer accordingly. To see the directory, input “yes”. If you input
“no”, the program will display a prompt asking for your desired theme. If the theme you
choose does not exist in the directory, a prompt will inform you of this and suggest you refer
to the directory to make sure your selection does exist. The program will then ask you to
make another selection. Remember to input the theme exactly as it is written in the directory
without adding a space or characters at the end.
4. The Physical Attribute
Once your selection is accepted, a prompt will enquire if you would like to add a
physical attribute to further filter the squad. If you choose not to add a physical attribute,
another prompt will ask if you wish to create your squad from the best or worst players in that
theme. Alternatively, if you decide to add a physical attribute, the program will first ask if you
wish to see the attribute directory. Once again, if you refuse to consult the directory and the
attribute you select does not exist, a prompt will suggest you refer to the attribute directory. If
you attribute is accepted, the program will then ask at what extreme in the attribute you wish
your players to be at. For example, if your attribute is height, it will ask if you would like a
team of the tallest or shortest players. If your attribute is a skill, like passing, it will ask if
would like a team of the worst or best passers. Remember to input the attribute exactly as it
is written in the directory without adding a space or characters at the end.
5. Filling the Gaps
Whether or not you’ve chosen to add an attribute, the program will proceed to begin
building the squad. If a position is empty, the program will prompt you replace the position
with another position. It is recommended that you replace that position with another in the
same field area. For instance, if the program states you are missing a left midfielder (LM), it
is recommended that you replace that position with another position in the midfield, such as
central midfielder (CM) or right midfielder (RM).
6. The Final XI
Once the squad is complete, the program will display a list of the players in the team
that the criteria that you have set.
You can consult the last page of this document for all directories and terminology needed to
operate this program.
Design Guide
The program is divided into three sections: the Files, which open the files containing
the data on which the program runs, the Functions, which sort the data based on the user’s
input, and the Procedure, which gathers the user’s input as well as orchestrate which
functions to run to yield the final result that the user requests.
The Files
The files containing the most important data are excel spreadsheets. In order to read
these spreadsheets, the csv module is imported at the very beginning of the program. All
regular .txt files are read with the typical open() function. In the case of the attributes.txt, a
dictionary was needed to be made so that the physical attribute that the user input can be
matched to an attribute in attributes.txt, verifying that the physical attribute the user has
chosen is legitimate.
The Functions
Several functions were created to handle different aspects of building the squad.
These functions mainly consist of if, while and for loops to handle the data piece by piece
as well as the assignment of new variables :

● sportposition(file, sport): Seeing as how this program is intended to be used
for a variety of sports, this function’s purpose is to return the positions of the
desired sport after having read them from file. It returns positionlist, a
template of the sport’s positions which is the backbone to building the team.

● countrysearch(file, category, R): This function is extremely important in
sorting data. Since there are nearly a thousand players in the player
database, countrysearch scans the file at row[R] for the desired category
and appends every match to a new list so that it returns a list of players who
all belong to the specified category. Because this new list is much smaller
than the original database, it is also much easier to use the data stored within
it.

● keywithmaxval(d), keywithminval(d): These functions are used to return the
key with the dictionary’s smallest or largest values.

● substitute(i): This function raises a prompt informing the user of a player
missing at a position and asks them for a replacement.

● FindBestPlayer(countrymen, team, i, Q): This function actually chooses the
players for the team. It begins by setting player as an empty variable. While
that variable is empty, two dictionaries are created. The program searches
through the shortlist from countrysearch. An if loop is used: if it finds a player
that plays in the position we want and is not already on the team, the player
and his rating (found at row Q) are appended to the first dictionary and the
player and his row index are append to the second. If the first dictionary is
empty, it means that there are no players for that position; substitute is run.
After scanning the shortlist, player is assigned to be the key first dictionary’s
maximum value, which is found using keywithmaxval(d). The player is then
removed from the shortlist using the row index stored in the second
dictionary. This is to make sure the same player does not appear twice in the
same team.

● FindWorstPlayer(countrymen, team, i, Q): This function works the same
way as FindBestPlayer, but uses keywithmaxval(d) to return the worst
player.

● BestTeamBuilder(countrymen, Q=0): Runs FindBestPlayer for every
position of the sport. It is defaulted at column Q=0, the column containing the
overall rating, in case a physical attribute is not specified.

● WorstTeamBuilder(countrymen, Q=0): Equivalent to BestTeamBuilder but
uses FindWorstPlayer.

● attributebuilder(refine, category): Once a physical attribute is specified, the
default Q value must be changed. The previously created attributedict is
used to find which column B the ratings for that attribute is. Once it is found,
the user must specify what extreme they want the attribute to be at: if the user
wants the attribute at its maximum, the team is built using BestTeamBuilder
with B instead of Q. Else, WorstTeamBuilder is run with B instead of Q.

● morefilters(refine): This function is run after the shortlist is created. It first
enquires if the user wants to add a physical attribute. An if loop is used: if
they do, the function then asks if they wish to see the attribute directory. As
with the previous directories, if the user refuses to consult the directory and
inputs an attribute that does not exist, the function will suggest that the user
consults the directory until they input an attribute that does exist. Once an
attribute is inputed, it is sent to attributebuilder to construct the team. If they
do not wish to add an attribute, the shortlist (labelled as refine) is sent to
either BestTeamBuilder or WorstTeamBuilder.

The Procedure

These are the actual steps followed by the program. It first prints a welcome
message and presents the available sports. A prompt then asks the user to select a sport
from the list. All inquisitive prompts in this program are created using the input() function. As
previously mentioned, this is the only input() function that is not case sensitive, since there
are many synonyms for “soccer”. A list is created of all these synonyms so that the program
knows which to accept and which to deny. The program then prints a template of the
positions of the sport. The final element in the procedure is an if nested in a while loop so
that the user selection for geographical theme is accepted or redirected to the directory.
From there, the procedure of the functions take course. Lastly, after the team is complete,
the players are printed in a vertical list so that this player list can be directly translated to the
Template initially created.

Terminology

Goalkeeping:
GK - Goalkeeper

Defense:
LB - Left Back
CB - Center Back
CB - Center Back
RB - Right Back

Midfield:
LM - Left Midfield
CM - Central Midfield
RM - Right Midfield

Attack:
LW - Left Wing
ST - Striker
RW - Right Win
