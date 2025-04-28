from flask import Flask, jsonify, request
import requests

app = Flask(__name__)

# A sample dictionary of some movies or shows for demonstration.
# In a real-world scenario, you might query a database or API.
movies_db = {
    "Inception": {
        "title": "Inception",
        "year": 2010,
        "genre": "Science Fiction",
        "rating": "8.8",
        "plot": "A thief who steals corporate secrets through the use of dream-sharing technology is given the inverse task of planting an idea into the mind of a CEO."
    },
    "The Dark Knight": {
        "title": "The Dark Knight",
        "year": 2008,
        "genre": "Action, Crime, Drama",
        "rating": "9.0",
        "plot": "When the menace known as The Joker emerges from his mysterious past, he wreaks havoc and chaos on the people of Gotham."
    },
    "Breaking Bad": {
        "title": "Breaking Bad",
        "year": 2008,
        "genre": "Crime, Drama, Thriller",
        "rating": "9.5",
        "plot": "A high school chemistry teacher turned methamphetamine producer partners with a former student to create and distribute high-quality meth."
    }
}

# Route for querying movie/show details
@app.route('/search', methods=['GET'])
def search_movie():
    query = request.args.get('query')
    
    if not query:
        return jsonify({"error": "No query parameter provided"}), 400
    
    # Try to find the movie in the database
    movie = movies_db.get(query)
    
    if movie:
        return jsonify(movie)
    else:
        # You can replace this with an API call to a service like TMDb or Open Movie Database.
        return jsonify({"error": "Movie/Show not found!"}), 404

# Route for movie recommendations (a simple example)
@app.route('/recommendations', methods=['GET'])
def get_recommendations():
    genre = request.args.get('genre')
    
    if not genre:
        return jsonify({"error": "No genre parameter provided"}), 400
    
    # Filter movies by genre (simplified)
    recommended_movies = [movie for movie in movies_db.values() if genre.lower() in movie['genre'].lower()]
    
    if recommended_movies:
        return jsonify(recommended_movies)
    else:
        return jsonify({"error": "No recommendations found for this genre."}), 404

if __name__ == '__main__':
    app.run(debug=True)

- 👋 Hi, I’m @sudarshan0910
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
sudarshan0910/sudarshan0910 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
