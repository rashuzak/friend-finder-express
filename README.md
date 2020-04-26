# Friend Finder - Node and Express Servers

Overview:

Building a compatibility-based "FriendFinder" application. This full-stack site will take in results from users' surveys, then compare their answers with those from other users. The app will then display the name and picture of the user with the best overall match.



* Check out [this demo version of the site](https://friend-finder-fsf.herokuapp.com/). Used  as a model for this assignment. 

*Created  `FriendFinder` folder. Inside the folder, we have directories as follows:

  ```
  FriendFinder
    - .gitignore
    - app
      - data
        - friends.js
      - public
        - home.html
        - survey.html
      - routing
        - apiRoutes.js
        - htmlRoutes.js
    - node_modules
    - package.json
    - server.js
  ```


Going to the localhost 3030 in the browser you will:

1. Click the 'submit' button to find a friend.

2. A survey page will open. Need to put your name and a link to your photo.

3. In the survey we have 10 questions. Each answer should be on a scale of 1 to 5 based on how much the user agrees or disagrees with a question.

    a.  `server.js` file require the basic npm packages: `express` and `path`.

    b.  `htmlRoutes.js` file include two routes:

         * A GET Route to `/survey` which displays the survey page.
         * A default, catch-all route that leads to `home.html` which displays the home page.

    c.  `apiRoutes.js` file contain two routes:

         * A GET route with the url `/api/friends`. (display a JSON of all possible friends).
         * A POST routes `/api/friends` (used to handle incoming survey results and route to handle the compatibility logic).

    d. Application's data is saved inside of `app/data/friends.js`   as an array of objects. 


6. Determine the user's most compatible friend using the following as a guide:

   * Convert each user's results into a simple array of numbers (ex: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`).
   * Then compare the difference between current user's scores against those from other users, question by question. Add up the differences to calculate the `totalDifference`.
     * Example:
       * User 1: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`
       * User 2: `[3, 2, 6, 4, 5, 1, 2, 5, 4, 1]`
       * Total Difference: **2 + 1 + 2 =** **_5_**
   * The absolute value of the differences is used. 
   * The closest match is the user with the least amount of difference.

7. Once found the current user's most compatible friend, a display of the result is a modal pop-up.
   * The modal displays both the name and picture of the closest match.

