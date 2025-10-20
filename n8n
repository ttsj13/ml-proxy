export default async function handler(request, response) {
  const { q } = request.query;

  if (!q) {
    return response.status(400).json({ error: 'Missing query parameter: q' });
  }

  try {
    const res = await fetch(
      `https://api.mercadolibre.com/sites/MLB/search?q=${encodeURIComponent(q)}`,
      {
        headers: {
          'User-Agent': 'Mozilla/5.0',
          'Accept': 'application/json',
        },
      }
    );

    if (!res.ok) {
      return response.status(res.status).json({ error: 'Mercado Livre API error' });
    }

    const data = await res.json();
    return response.status(200).json(data);
  } catch (error) {
    return response.status(500).json({ error: 'Internal Server Error', details: error.message });
  }
}
